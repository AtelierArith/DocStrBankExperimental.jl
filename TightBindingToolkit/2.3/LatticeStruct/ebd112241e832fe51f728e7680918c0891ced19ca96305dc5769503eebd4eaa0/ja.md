`Lattice{T}` は、`UnitCell{T}` から構築された一般的な実空間格子を表すデータ型です。

# 属性

  * `uc          ::  UnitCell{T}`: 格子の単位セル。
  * `size        ::  Vector{Int64}`: UnitCell `primitives` の単位での格子のサイズ。
  * `length      ::  Int64`: サイトの総数。
  * `sites       ::  Dict{ Tuple{Int64, Vector{Int64}}, Int64}` : キーが (サブ格子, オフセット) で、対応する値が格子上のサイト番号である辞書。
  * `positions   ::  Vector{ Vector{Float64}}`: すべての格子サイトの実空間位置。
  * `fields      ::  Vector{ Vector{Float64}}`: すべての格子サイトのフィールド。
  * `bondSites   ::  Matrix{Int64}`: `lattice.length` 行を持つ行列で、`bondSites[s, i]` は格子上のサイト-s の i 番目の隣接サイトの番号です。
  * `bondDists   ::  Matrix{Float64}`: `lattice.length` 行を持つ行列で、`bondDists[s, i]` は格子上のサイト-s の i 番目の隣接サイトまでの距離です。
  * `bondLabels  ::  Matrix{String}`: `lattice.length` 行を持つ行列で、`bondLabels[s, i]` は格子上のサイト-s の i 番目の隣接サイトへの結合のラベルです。
  * `bondMats    ::  Matrix{Array{ComplexF64, T}}`: `lattice.length` 行を持つ行列で、`bondMats[s, i]` は格子上のサイト-s の i 番目の隣接サイトに接続する結合の `Array{ComplexF64, T}` です。

この構造体は次のように初期化します。

```julia
Lattice( uc::UnitCell{T}, size::Vector{Int64} ; null_dist::Float64 = -1.0, null_label::String = "-")
```

ここで、`null_dist` と `null_label` は、与えられた境界条件により許可されていない結合に使用されますが、コード内では追跡されます。
