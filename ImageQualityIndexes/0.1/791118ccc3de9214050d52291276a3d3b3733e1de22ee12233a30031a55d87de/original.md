```
SSIM([kernel], [(α, β, γ)]) <: FullReferenceIQI
assess(iqi::SSIM, img, ref)
assess_ssim(img, ref)
```

Structural similarity (SSIM) index is an image quality assessment method based on degradation of structural information.

The SSIM index is composed of three components: luminance, contrast, and structure; `ssim = 𝐿ᵅ * 𝐶ᵝ * 𝑆ᵞ`, where `W := (α, β, γ)` controls relative importance of each components. By default `W = (1.0, 1.0, 1.0)`.

In practice, a mean version SSIM is used. At each pixel, SSIM is calculated locally with neighborhoods weighted by `kernel`, returning a ssim map; `ssim` is actaully `mean(ssim_map)`. By default `kernel = KernelFactors.gaussian(1.5, 11)`.

!!! info
    SSIM is defined only for gray images. RGB images are treated as 3d Gray images. General `Color3` images are converted to RGB images first, in which case, you could manually expand them using `channelview` if you don't want them converted to RGB first.


# Example

`ssim(img, ref)` should be sufficient to get a benchmark for algorithms. One could also instantiate a customed SSIM, then pass it to `assess` or use it as a function. For example:

```julia
iqi = SSIM(KernelFactors.gaussian(2.5, 17), (1.0, 1.0, 2.0))
assess(iqi, img, ref)
iqi(img, ref)
```

# Reference

[1] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2004). Image quality assessment: from error visibility to structural similarity. *IEEE transactions on image processing*, 13(4), 600-612.

[2] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2003). The SSIM Index for Image Quality Assessment. Retrived May 30, 2019, from http://www.cns.nyu.edu/~lcv/ssim/
