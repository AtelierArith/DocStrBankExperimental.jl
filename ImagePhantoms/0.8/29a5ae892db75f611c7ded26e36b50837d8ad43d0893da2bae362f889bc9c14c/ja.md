```
radon(r::Vector, ϕ::RealU, oa::Array{<:Object2d})
```

1つの`ϕ`値に対して、`r`位置のグリッドでサンプリングされた平行ビーム投影を返します。返される配列のサイズは`length(r)`です。
