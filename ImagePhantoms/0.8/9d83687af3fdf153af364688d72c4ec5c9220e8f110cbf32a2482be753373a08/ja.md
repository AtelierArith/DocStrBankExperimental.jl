```
radon(u:Vector, v:Vector, ϕ:RealU, θ:RealU, oa::Array{<:Object3d})
```

与えられた `(ϕ,θ)` ペアに対して、`(u,v)` の位置のグリッドでサンプリングされた平行ビーム投影ビューを返します。返される配列のサイズは `length(u) × length(v)` です。
