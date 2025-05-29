```
SSIM([kernel], [(α, β, γ)]; crop=false) <: FullReferenceIQI
assess(iqi::SSIM, img, ref)
assess_ssim(img, ref; crop=false)
```

Structural similarity (SSIM) index is an image quality assessment method based on degradation of structural information.

The SSIM index is composed of three components: luminance, contrast, and structure; `ssim = 𝐿ᵅ * 𝐶ᵝ * 𝑆ᵞ`, where `W := (α, β, γ)` controls relative importance of each components. By default `W = (1.0, 1.0, 1.0)`.

In practice, a mean version SSIM is used. At each pixel, SSIM is calculated locally with neighborhoods weighted by `kernel`, returning a ssim map; `ssim` is actaully `mean(ssim_map)`. By default `kernel = KernelFactors.gaussian(1.5, 11)`.

!!! tip
    The default parameters comes from [1]. For benchmark usage, it is recommended to not change the parameters, because most other SSIM implementations follows the same settings. Keyword `crop` controls whether the boundary of ssim map should be dropped; you need to set it `true` to reproduce the result in [1].


# Example

`assess_ssim(img, ref)` should be sufficient to get a benchmark for algorithms. One could also instantiate a customed SSIM, then pass it to `assess` or use it as a function. For example:

```julia
iqi = SSIM(KernelFactors.gaussian(2.5, 17), (1.0, 1.0, 2.0))
assess(iqi, img, ref)
iqi(img, ref) # both usages are equivalent
```

!!! info
    SSIM is defined only for gray images. How `RGB` and other `Color3` images are handled may vary in different implementations. For `RGB` images, channels are handled seperately when calculating 𝐿, 𝐶, and 𝑆. Generic `Color3` images are converted to `RGB` first before calculation.


# Reference

[1] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2004). Image quality assessment: from error visibility to structural similarity. *IEEE transactions on image processing*, 13(4), 600-612.

[2] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2003). The SSIM Index for Image Quality Assessment. Retrived May 30, 2019, from http://www.cns.nyu.edu/~lcv/ssim/
