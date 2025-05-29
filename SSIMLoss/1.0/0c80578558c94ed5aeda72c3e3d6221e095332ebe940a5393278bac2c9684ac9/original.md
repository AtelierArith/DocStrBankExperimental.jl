```
ssim(x, y, kernel=ssim_kernel(x); peakval=1, crop=true, dims=:)
```

Return the [structural similarity index measure](https://en.wikipedia.org/wiki/Structural_similarity) (SSIM) between two signals. SSIM is computed via the mean of a sliding window of statistics computed between the two signals. By default, the sliding window is a Gaussian with side-length 11 in each signal dimension and σ=1.5. `crop=false` will pad `x` and `y`  such that the sliding window computes statistics centered at every pixel of the input (via same-size convolution).  `ssim` computes statistics independently over channel and batch dimensions. `x` and `y` may be 3D/4D/5D tensors with channel and batch-dimensions.

`peakval=1` is the standard for image comparisons, but in practice should be set to the maximum value of your signal type. 

`dims` determines which dimensions to average the computed statistics over. If `dims=1:ndims(x)-1`, SSIM will be computed for each batch-element separately.

The results of `ssim` are matched against those of [ImageQualityIndexes](https://github.com/JuliaImages/ImageQualityIndexes.jl) for grayscale and RGB images (i.e. x, y both of size (N1, N2, 1, B) and (N1, N2, 3, B) for grayscale and color images, resp.).

See also [`ssim_loss`](@ref), [`ssim_loss_fast`](@ref).
