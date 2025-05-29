```
grad_y, grad_x, mag, orient = imedge(img, kernelfun=KernelFactors.ando3, border="replicate")
```

エッジ検出フィルタリング。 `kernelfun` は [`imgradients`](@ref) に対して有効なカーネル関数で、デフォルトは [`KernelFactors.ando3`](@ref) です。 `border` は `padarray` で指定された境界条件のいずれかです。

タプル `(grad_y, grad_x, mag, orient)` を返し、これはそれぞれ水平勾配、垂直勾配、最も強いエッジの大きさと方向です。
