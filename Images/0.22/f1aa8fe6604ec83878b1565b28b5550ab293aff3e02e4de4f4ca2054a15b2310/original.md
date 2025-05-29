```
thres = otsu_threshold(img)
thres = otsu_threshold(img, bins)
```

Computes threshold for grayscale image using Otsu's method.

Parameters:

  * img         = Grayscale input image
  * bins        = Number of bins used to compute the histogram. Needed for floating-point images.
