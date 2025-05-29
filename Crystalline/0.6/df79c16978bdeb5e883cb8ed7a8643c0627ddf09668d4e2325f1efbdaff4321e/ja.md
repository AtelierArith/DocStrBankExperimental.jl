```
find_isomorphic_parent_pointgroup(g::AbstractVector{SymOperation{D}}) 
                                                --> PointGroup{D}, Vector{Int}, Bool
```

グループ `g`（またはグループを定義する演算子のコレクション）を与えると、`g` と同型の「親」点群を特定します。

返される変数は次のとおりです：

  * `pg`: `g` の演算子のソートに一致するようにソートされた演算子を持つ、特定された「親」点群。
  * `Iᵖ²ᵍ`: 標準の点群演算のソート（[`pointgroup(::String)`](@ref) によって返される）を `g` の演算子のソートに変換する置換ベクトル。
  * `equal`: 点群の部分が同一であるか（`true`）または単に `g` の点群演算に同型であるかを識別するブール値。実際には、これにより `pg` と `g` が同じ設定にあるかどうかが示されます。

## 実装

同定は、演算子の比較に基づいて部分的に行われます（これは `equal = true` の場合に十分です）および部分的に乗法表の比較に基づいて行われます（`equal = false` の場合）。後者は、演算子のソートが不運な場合（すなわち、`g` と `pg` のソート間の置換が多くのペアワイズ置換によって異なる場合）に組合せ的に遅くなる可能性があります。

単なる乗法表の同型を超えて、検索は `pg` と `g` の間で全ての回転順序が共有されることも保証します。同様に、回転の感覚（例：4⁺と4⁻は反対の回転感覚または方向を持つ）は共有されます。これにより、内在的に互いに同型である点群（例："m" と "-1"）が明確に区別されますが、空間的解釈が異なる場合があります。

## 特性

次の特性が `g`、`pg`、および `Iᵖ²ᵍ` に対して成り立ちます：

```jl
pg, Iᵖ²ᵍ, equal = find_isomorphic_parent_pointgroup(g)
@assert MultTable(pg) == MultTable(pointgroup(g))
pg′ = pointgroup(label(pg), dim(pg)) # "標準" ソート
@assert pg′[Iᵖ²ᵍ] == pg
```

`equal = true` の場合、次のことも成り立ちます：

```jl
pointgroup(g) == operations(pg) == operations(pg′)[Iᵖ²ᵍ]
```

## 例

```jl
sgnum = 141
wp    = wyckoffs(sgnum, Val(3))[end] # 4a Wyckoff 位置
sg    = spacegroup(sgnum, Val(3))
siteg = sitegroup(sg, wp)
pg, Iᵖ²ᵍ, equal = find_isomorphic_parent_pointgroup(siteg)
```
