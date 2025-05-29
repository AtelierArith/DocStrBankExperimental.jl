```
kernel_gradient( k::AbstractSPHKernel, h_inv::Real, xᵢ::T, xⱼ::T ) where T
```

カーネル `k` の勾配を隣接点 `xⱼ` の位置で計算します。

$$
∇W(x_{ij}, h_i) = \frac{dW}{dx}\vert_{x_j} \frac{Δx_{ij}}{||x_{ij}||} \frac{1}{h_i}
$$

```

```
