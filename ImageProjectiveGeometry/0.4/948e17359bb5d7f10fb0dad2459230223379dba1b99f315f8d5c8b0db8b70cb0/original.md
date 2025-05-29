grey2census - Convert image grey scale values to census values

```
Usage:  cimg = grey2census(img, window)

Arguments:
          img - greyscale image to be processed
       window - Optional 2-vector [rows,cols] specifying the size of the
                window to be considered in computing the census
                transform. Defaults to [7, 9].  The values must be odd and
                their product must not be greater than 64.
Returns:
         cimg - Census encoded UInt64 image.
```

Each pixel is encoded with a bit pattern formed by comparing the pixel with the pixels in the window around it. If a window pixel is less than the centre pixel its corresponding bit in the census encoding is set.  This provides an encoding that describes a pixel in terms of its surrounding pixels in a way that is invariant to lighting variations.  Note, however, that the encoding is dependent on the image orientation.

Use the Hamming distance to compare encoded pixel values when matching.

```
  hammingDist = count_ones(img1[r,c] $ img2[r,c])
```
