```
𝒲( k::AbstractSPHKernel, h_inv, xᵢ, xⱼ)
```

隣接点 `xⱼ` の位置でカーネル `k` の値を計算します。

$$
W(\vec{x}_i - \vec{x}_j, h_i)
$$
