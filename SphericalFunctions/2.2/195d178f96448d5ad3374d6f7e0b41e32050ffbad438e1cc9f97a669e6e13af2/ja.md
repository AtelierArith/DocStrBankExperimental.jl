```
clenshaw_curtis_rings(N, [T=Float64])
```

クレンズショー・カーティス則による積分に適したコラティチュード座標の値（$θ$）で、[`clenshaw_curtis`](@ref)によって提供される重みを使用します。

この関数への最初の引数は `N` であり、他のいくつかの関数で使用される `ℓₘₐₓ` ではないことに注意してください。スピン重み付き球面調和関数の場合、`N=2ℓₘₐₓ+1` を使用することをお勧めします。
