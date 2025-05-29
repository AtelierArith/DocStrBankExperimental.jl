```julia
tetunsuitable!(unsuitable; check_signature)

```

Cラッパーから呼び出されるtetunsuitable関数を設定します。この関数を設定することは、tetrahedralizeへの1回の後続呼び出しに対してのみ有効です。渡すべき関数のシグネチャは次のとおりです。

```
unsuitable(p1::Vector{Float64},p2::Vector{Float64},p3::Vector{Float64},p4::Vector{Float64})::Bool
```

ここで`p1...p4`は四面体のコーナーを記述する3ベクトルであり、戻り値はその体積が大きすぎると見なされる場合に`true`です。
