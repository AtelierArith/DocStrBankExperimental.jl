```
ssim_loss_fast(x, y; kernel_length=5, peakval=1, crop=true, dims=:)
```

Computes `ssim_loss` with an averaging kernel instead of a large Gaussian kernel for faster computation. `kernel_length` specifies the averaging kernel side-length in each signal dimension of x, y.  See [`ssim`](@ref) for a detailed description of SSIM and the above arguments. 

See also [`ssim_loss`](@ref).
