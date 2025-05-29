```
kernel_deriv(kernel::AbstractSPHKernel, u::Real, h_inv::Real) where T
```

位置 $u = \frac{x}{h}$ でのカーネルの導関数を評価します。
