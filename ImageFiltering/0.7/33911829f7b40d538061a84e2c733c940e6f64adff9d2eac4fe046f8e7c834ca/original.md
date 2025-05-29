imgradients(img, kernelfun=KernelFactors.ando3, border="replicate") -> gimg1, gimg2, ...

Estimate the gradient of `img` in the direction of the first and second dimension at all points of the image, using a kernel specified by `kernelfun`.

Returns a tuple-of-arrays, `(gimg1, gimg2, ...)`, one for each dimension of the input: `gimg1` corresponds to the derivative with respect to the first dimension, `gimg2` to the second, and so on.

## Example

```julia
using Images, ImageFiltering, TestImages
img = testimage("mandrill")
imgr = imgradients(img, KernelFactors.sobel, "reflect")
mosaicview(imgr...)
```
