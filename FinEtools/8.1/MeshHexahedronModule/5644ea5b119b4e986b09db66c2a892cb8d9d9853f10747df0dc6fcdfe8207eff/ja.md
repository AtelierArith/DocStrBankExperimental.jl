```
H8hexahedron(xyz::Matrix{T}, nL::IT, nW::IT, nH::IT; blockfun = nothing) where {T<:Number, IT<:Integer}
```

頂点の位置によって与えられる一般的なヘキサヘドロンのメッシュ。

`xyz` = 各行に1つの頂点位置; 2行（その隅によって与えられる長方形ブロックの場合）または8行（一般的なヘキサヘドロン）。 `nL`, `nW`, `nH` = 各方向の要素数 `blockfun` = オプションの引数: ブロック生成メッシュ関数の関数（`H8block()`関数のシグネチャを持つ）。
