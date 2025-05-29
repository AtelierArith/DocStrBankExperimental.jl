```
kernel_value( k::AbstractSPHKernel, h_inv::Real, 
              xᵢ::Real, xⱼ::Real )
```

隣接点 `xⱼ` の位置でカーネル `k` の値を計算します。

$$
W(x_i - x_j, h_i)
$$
