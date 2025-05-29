```
global_position(g::BVHGraph, v::Integer, f::Integer, N::Matrix{Float64} = Matrix(1.0I, 4, 4))
```

頂点 `v` のフレーム `f` に対するグローバル位置を返します。

この関数は結果を `g` に保存しません。`N` は変更されるべきではありません。

参照: [`global_positions!`](@ref)
