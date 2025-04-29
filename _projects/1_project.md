---
layout: page
title: Demosaicing in C++
description: See <a href="https://github.com/rkitichotkul/demosaic">GitHub repository</a>
img: assets/img/demosaic/mosaic.jpg
importance: 1
category: work
related_publications: false
---

Digital cameras capture images using sensors overlaid with a color filter array, most commonly the Bayer pattern. Each pixel records only one color channel --- red, green, or blue --- requiring a process called *demosaicing* to reconstruct a full-color image. As part of a recent project, I developed a C++ engine to simulate the Bayer pattern and perform demosaicing via OpenCV’s <a href="https://docs.opencv.org/3.4/de/d25/imgproc_color_conversions.html">`cvtColor`</a> function.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="https://github.com/rkitichotkul/demosaic/blob/main/assets/plush_rggb.jpg" title="Simulated RAW image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="https://github.com/rkitichotkul/demosaic/blob/main/assets/plush_sim_demosaiced.jpg" title="Demosaiced image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="https://github.com/rkitichotkul/demosaic/blob/main/assets/mosaic.jpg" title="Zoomed-in Bayer pattern" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Demosaicing demonstration using a photo of my desk. (Left) Simulated RAW image from RGGB Bayer pattern. (Middle) Demosaiced image. (Right) Zoomed-in RAW image with overlaid Bayer pattern.
</div>

I used <a href="https://www.libraw.org/">LibRaw</a> to read real RAW images, enabling the engine to process actual sensor data. Demosaicing alone, however, is not sufficient to produce accurate color for real RAW images. Additional steps like black level correction, white balancing, and gamma adjustment are likely necessary.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="https://github.com/rkitichotkul/demosaic/blob/main/assets/plush_realraw_grayscale.jpg" title="Real RAW image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="https://github.com/rkitichotkul/demosaic/blob/main/assets/plush_real_demosaiced.jpg" title="Demosaiced image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Demosaicing a real RAW image. My Fujifilm X-A3 allows saving both .jpg and RAW (as .RAF) simultaneously. (Left) Real RAW image. (Right) Demosaiced image.
</div>

There could be future updates with other parts of the Image Signal Processing pipeline.