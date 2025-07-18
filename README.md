
#  MyGallery - Apache Tomcat Web Server Project

This project demonstrates the configuration and performance evaluation of a web server using Apache Tomcat. It hosts a gallery-style web service with 5 HTML pages containing photos in various layouts, accessible from both a local system and mobile device.

## Project Overview

- **Web Server:** Apache Tomcat 9.0.107  
- **Platform:** macOS (MacBook Pro)  
- **Port:** 8080  
- **Access URL:** `http://localhost:8080/mygallery/index.html`

## Web Pages Created

| Page         | Description                        |
|--------------|------------------------------------|
| `index.html` | Home page with hyperlinks to other pages |
| `page1.html` | 4 photos (2x2 grid)                |
| `page2.html` | 2 photos in a row                  |
| `page3.html` | 1 large photo                      |
| `page4.html` | 6-photo grid                       |
| `page5.html` | Mixed layout (row + centered + wide) |

## Mobile Access

The gallery was successfully accessed from a mobile phone using the local IP and port. Screenshots confirm that all pages rendered correctly on the remote client.

## Performance Testing

### Benchmark Commands

- `ab -n 1000 -c 10 http://localhost:8080/mygallery/page1.html`
- `ab -n 100 -c 1 http://localhost:8080/mygallery/page1.html`

### Results Summary

| Test Description            | Requests/sec | Avg Time/Request | Throughput |
|----------------------------|--------------|------------------|------------|
| 1000 req, 10 concurrency   | 15814.53     | 0.063 ms         | ~9003.78 KB/s |
| 100 req, 1 concurrency     | 2396.07      | 0.417 ms         | ~1364.17 KB/s |

## Stress Test

### Attempted: 
`ab -n 10000 -c 500`  

- Failed: Too many open files (macOS limit)

### Succeeded: 
`ab -n 5000 -c 100`  

- 26302.78 req/sec  
- Avg request time: 3.802 ms  
- Throughput: ~14975.12 KB/s  


##  Setup Instructions (Quick Start)

1. Download and extract Apache Tomcat: https://tomcat.apache.org/download-90.cgi
2. Place your HTML files in `webapps/mygallery/`
3. Start the server with `startup.sh`
4. Visit: `http://localhost:8080/mygallery/index.html`

## Folder structure 

<pre lang="markdown"> ``` tomcat9/ └── webapps/ └── mygallery/ ├── index.html ├── page1.html ├── page2.html ├── page3.html ├── page4.html ├── page5.html └── images/ ├── pic1.jpg ├── pic2.jpg ├── pic3.jpg ├── pic4.jpg ├── pic5.jpg └── pic6.jpg ``` </pre>
