grey2lbp - Convert image grey scale values to local binary pattern.

```
Usage:  lbpim = grey2lbp(img, rc, window)

Arguments:
          img - greyscale image to be processed
           rc - [2 x 2*nPairs] array of integer (row;col) coordinates.
                Each successive pair of columns provides a pair of
                points for comparing image grey values against each other
                for forming a binary descriptor of a patch about some
                central feature location. Array rc must not have more than
                128 columns corresponding to an encoding of 64 bits,
       window - 2-vector specifying the size of the window to be considered
                in computing the local standard deviation for determining
                regions to be encoded with a 0.  The window size values
                should match the range of values in rc and be odd.

Returns:
        lbpim - Local Binary Pattern encoded UInt64 image.
```

Each pixel is encoded with a bit pattern formed by comparing pairs of pixels. If the difference between pixels is -ve they are are encoded with 1, else 0. This provides an encoding that describes a pixel in terms of its surrounding pixels in a way that is invariant to lighting variations.  Note, however, that the encoding is dependent on the image orientation.   The encoding is also sensitive to noise on near constant regions.

Use the Hamming distance to compare encoded pixel values when matching.

See also: grey2lbp!(), grey2census(), briefcoords()
