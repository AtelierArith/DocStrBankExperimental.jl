```
MSSSIM([kernel], [W]; num_scales = length(W)) <: FullReferenceIQI
assess(iqi::MSSSIM, img, ref)
assess_msssim(img, ref; num_scales = 5)
```

Computes the multi-scale structural similarity (MS-SSIM) between two images.

!!! tip
    The default parameters comes from [1]. For benchmark usage, it is recommended to not change the parameters, because most other SSIM implementations follows the same settings.


# Examples

For benchmark usage, it is recommended to use `assess_msssim(img, ref)`. One could also create a custom `MSSSIM` instance and then pass it to `assess` or use it as a function.

```julia
iqi = MSSSIM(KernelFactors.gaussian(2.5, 17), (1.0, 1.0, 2.0)./4)
assess(iqi, img, ref)
iqi(img, ref) # both usages are equivalent
```

# Reference

[1] Wang, Z., Simoncelli, E. P., & Bovik, A. C. (2003, November). Multiscale structural similarity for image quality assessment.In *The Thrity-Seventh Asilomar Conference on Signals, Systems & Computers*, 2003 (Vol. 2, pp. 1398-1402). Ieee.

[2] Wang, Z. IW-SSIM: Information Content Weighted Structural Similarity Index for Image Quality Assessment. Retrived July 9, 2020, from https://ece.uwaterloo.ca/~z70wang/research/iwssim/

[3] Jorge Pessoa. pytorch-msssim. Retrived July 9, 2020, from https://github.com/jorge-pessoa/pytorch-msssim
