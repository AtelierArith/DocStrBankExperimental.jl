```
radon(u:Vector, v:Vector, ϕ:Vector, θ:Vector, oa::Array{<:Object3d})
```

グリッドの `(u,v,ϕ,θ)` 位置でサンプリングされた平行ビーム投影を返します。返される配列のサイズは `length(u) × length(v) × length(ϕ) × length(θ)` です。
