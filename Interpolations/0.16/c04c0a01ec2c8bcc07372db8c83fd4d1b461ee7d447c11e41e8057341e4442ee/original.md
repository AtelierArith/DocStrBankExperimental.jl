```
Lanczos{N}(a=4)
```

Lanczos resampling via a kernel with scale parameter `a` and support over `N` neighbors.

This form of interpolation is merely the discrete convolution of the samples with a Lanczos kernel of size `a`. The size is directly related to how "far" the interpolation will reach for information, and has `O(N^2)` impact on runtime. An alternative implementation matching `lanczos4` from OpenCV is available as Lanczos4OpenCV.
