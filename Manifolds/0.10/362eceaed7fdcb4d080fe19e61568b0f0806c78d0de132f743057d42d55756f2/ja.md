```
manifold_dimension(M::KendallsShapeSpace)
```

[`KendallsShapeSpace`](@ref) マニフォールド `M` の次元を返します。次元は、通常の場合 $k \geq n+1$ のときは $n(k - 1) - 1 - n(n - 1)/2$ で与えられ、それ以外の場合は $(k + 1)(k - 2) / 2$ です。ただし、$k$ が 1 の場合は次元は 0 になります。過剰次元の場合については [Kendall:1984](@cite) を参照してください。
