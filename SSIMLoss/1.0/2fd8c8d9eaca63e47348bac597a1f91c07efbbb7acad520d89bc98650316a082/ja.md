```
ssim_loss_fast(x, y; kernel_length=5, peakval=1, crop=true, dims=:)
```

大きなガウスカーネルの代わりに平均化カーネルを使用して、より高速に計算する `ssim_loss` を計算します。 `kernel_length` は、x、y の各信号次元における平均化カーネルの辺の長さを指定します。 SSIM と上記の引数の詳細な説明については、[`ssim`](@ref) を参照してください。

また、[`ssim_loss`](@ref) も参照してください。
