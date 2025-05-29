```
segments                = meanshift(img, spatial_radius, range_radius; iter=50, eps=0.01))
```

Segments the image using meanshift clustering. Returns a `SegmentedImage`.

Parameters:

  * img                            = input grayscale image
  * spatial*radius/range*radius    = bandwidth parameters of truncated normal kernel. Controlling the size of the kernel determines the resolution of the mode detection.
  * iter/eps                       = stopping criterion for meanshift procedure. The algorithm stops after iter iterations or if kernel center moves less than eps distance in an update step, whichever comes first.
