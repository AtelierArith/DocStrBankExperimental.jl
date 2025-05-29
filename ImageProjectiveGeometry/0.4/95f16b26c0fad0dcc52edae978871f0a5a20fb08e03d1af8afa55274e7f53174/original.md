histtruncate - Truncates ends of an image histogram.

Function truncates a specified percentage of the lower and upper ends of an image histogram.

This operation allows grey levels to be distributed across the primary part of the histogram.  This solves the problem when one has, say, a few very bright values in the image which have the overall effect of darkening the rest of the image after rescaling.

```
Usage:
1)   newimg = histtruncate(img, lHistCut, uHistCut)
2)   newimg = histtruncate(img, HistCut)

Arguments:
 Usage 1)
   img         -  Image to be processed.
   lHistCut    -  Percentage of the lower end of the histogram
                  to saturate.
   uHistCut    -  Percentage of the upper end of the histogram
                  to saturate.  If omitted or empty defaults to the value
                  for lHistCut.
 Usage 2)
   HistCut     -  Percentage of upper and lower ends of the histogram to cut.

Returns:
   newimg      -  Image with values clipped at the specified histogram
                  fraction values.  If the input image was colour the
                  lightness values are clipped and stretched to the range
                  0-1.  If the input image is greyscale no stretching is
                  applied. You may want to use imgnormalise() to achieve this.
```

See also: imgnormalise()
