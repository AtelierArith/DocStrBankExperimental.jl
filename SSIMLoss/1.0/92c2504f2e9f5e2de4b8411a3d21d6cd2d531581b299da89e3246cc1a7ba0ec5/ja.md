```
ssim_kernel(x::AbstractArray{T, N}) where {T, N}
```

σ=1.5およびサイドレングス11のガウスカーネルを[`ssim`](@ref)で使用するために返します。返される配列は`x`と同じデバイス上にあります。
