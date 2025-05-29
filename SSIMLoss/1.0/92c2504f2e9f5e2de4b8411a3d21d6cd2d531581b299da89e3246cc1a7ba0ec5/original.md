```
ssim_kernel(x::AbstractArray{T, N}) where {T, N}
```

Return Gaussian kernel with σ=1.5 and side-length 11 for use in [`ssim`](@ref).  Returned array will be on the same device as `x`.
