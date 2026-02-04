# EPUB Sample for JPEG XL (JXL) Compatibility Testing

## Overview
This repository provides a test EPUB file and its source materials to support the ongoing discussion about including JPEG XL (JXL) as a Core Media Type in EPUB 3.4 (w3c/epub-specs #2899).

While JPEG XL offers superior compression efficiency and advanced image features, rendering results can vary among current reading systems depending on the encoding tools and options used.
The purpose of this project is not to advocate for or against any specific tool, but to share implementation results that may inform discussions on future compatibility and specification development.
## Test Configuration
Starting from a 1440 × 1920 px PNG source image, this test EPUB (OPF version 3.0) includes JXL files generated using the following four methods:

### 1. Conversion via ImageMagick
* __Characteristic__: Expected to have relatively broad compatibility.
~~~
$ convert org.png -define jxl:effort=7 out.jxl
~~~
### 2. Conversion via cjxl (Reference Encoder)
* __Characteristic__: Generated using the official reference encoder. It achieves dramatic file size reduction in lossless modes; supporting this format is crucial for reducing the data footprint of digital books.
~~~
$ cjxl org.png out.jxl
~~~
### 3. Export via Adobe Photoshop
* __Characteristic__: Verification of a workflow using standard plugins/features in commercial production environments.
### 4. Export via GIMP
* __Characteristic__: Verification of export precision within an open-source production environment.

### Summary of Current Findings (as of February 2026)
* __ImageMagick (1)__: Successfully rendered in many readers, demonstrating relatively good compatibility.
* __cjxl / Photoshop / GIMP (2, 3, 4)__: Currently face rendering challenges in many reading environments, resulting either in no display or the triggering of defined fallback images.

This repository aims to provide concrete testing materials for implementers and specification authors, contributing to improved interoperability and media format support in future EPUB releases.
