```
kernel_value( k::AbstractSPHKernel, h_inv::T1, 
                   xᵢ::T2, xⱼ::T2 ) where {T1,T2}
```

隣接点 `xⱼ` の位置でのカーネル `k` の値を計算します。

$$
W(\vec{x}_i - \vec{x}_j, h_i)
$$
