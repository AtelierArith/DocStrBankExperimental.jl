```
radon(r::Vector, ϕ::Vector, oa::Array{<:Object2d})
```

グリッドの `(r,ϕ)` 位置でサンプリングされた平行ビーム2Dシノグラムを返します。返される配列のサイズは `length(r) × length(ϕ)` です。
