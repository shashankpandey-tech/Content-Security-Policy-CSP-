# Content-Security-Policy
Content Security Policy (CSP)

Index.html (Angulat 8)

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Content-Security-Policy</title>
    <meta name="viewport" content="width=device-width">
    <meta http-equiv="Content-Security-Policy" 
        content="default-src 'self' data: gap: 'unsafe-eval' ws: ; 
        style-src 'self' 'unsafe-inline'; 
        script-src https: *.example.com ;
        media-src 'none'; 
        font-src *;
        connect-src *;
        img-src 'self' data: content:;">
        <!--
        Also
        base-uri /abc/; - limit to content in this folder  v2
        form-action ; - limit where forms can be sent  v2
        
        VALUES
        'self' - anything from the same origin
        data: - data-uri (base64 images)
        gap: - phonegap and cordova used by plugins on iOS
        ws: - web sockets
        * - anything except data: and blobs
        filesystem: - access things on the local filesystem
        blob: - allow Binary Large OBjects
        mediastream: - allow streamed media
        content: - used by Cordova
        'none' - prevent anything in the category
        https: - anything over https://
        *.example.com - anything from any subdomain of example.com
        'unsafe-inline' - inline source elements like style attribute, onclick, or script tags 
        'unsafe-eval' - allow javascript eval( ). 
        -->
    <link rel="stylesheet" href="main.css">
</head>
<body>
    <h1>Content-Security-Policy</h1>
    
    <p style="" onclick="">The real value of this page is the stuff in the &lt;head&gt;</p>
    
    <p>When building apps with Cordova we have to make sure that we are adding the Content-Security-Policy information into the &lt;head&gt;.</p>
    
    <p>We can also add this header to any webpage to add a layer of security which will control what resources can be loaded and from which sources.</p>
    
    <p>Official Reference: <a href="https://content-security-policy.com/">https://content-security-policy.com/</a></p>
</body>
</html>

# What is CSP ?

Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross-Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft, to site defacement, to malware distribution.

CSP is designed to be fully backward compatible (except CSP version 2 where there are some explicitly-mentioned inconsistencies in backward compatibility; more details here section 1.1). Browsers that don't support it still work with servers that implement it, and vice versa: browsers that don't support CSP ignore it, functioning as usual, defaulting to the standard same-origin policy for web content. If the site doesn't offer the CSP header, browsers likewise use the standard same-origin policy.

To enable CSP, you need to configure your web server to return the Content-Security-Policy HTTP header. (Sometimes you may see mentions of the X-Content-Security-Policy header, but that's an older version and you don't need to specify it anymore.)

More... https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP

