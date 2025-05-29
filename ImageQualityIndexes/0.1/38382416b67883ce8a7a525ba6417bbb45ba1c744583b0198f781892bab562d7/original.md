```
PSNR <: FullReferenceIQI
assess(PSNR(), x, ref, [, peakval])
assess_psnr(x, ref [, peakval])
```

Peak signal-to-noise ratio (PSNR) is used to measure the quality of image in present of noise and corruption.

For gray image `x`, PSNR (in dB) is calculated by `10log10(peakval^2/mse(x, ref))`, where `peakval` is the maximum possible pixel value of image `ref`. `x` will be converted to type of `ref` when necessary.

Generally, for non-gray image `x`, PSNR is reported against each channel of `ref` and outputs a `Vector`, `peakval` needs to be a vector as well.

!!! info
    Conventionally, `m×n` rgb image is treated as `m×n×3` gray image. To calculated channelwise PSNR of rgb image, one could pass `peakval` as vector, e.g., `psnr(x, ref, [1.0, 1.0, 1.0])`

