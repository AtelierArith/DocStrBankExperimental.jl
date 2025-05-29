```
kernel_gradient( k::AbstractSPHKernel, r::T1, h_inv::T1, Δx::T2) where {T1,T2}
```

カーネル `k` の勾配を、隣接点 `j` の距離ベクトル `Δx` に沿った距離 `r` で計算します。

$$
∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}
$$

```

```
