```
BoundaryConditionCoupled(other_semi_index, indices, uEltype, coupling_converter)
```

2つのメッシュを接合するための境界条件。別のメッシュの境界での解の値が境界値として使用されます。これには[`SemidiscretizationCoupled`](@ref)の使用が必要です。別のメッシュは、半離散化のタプル内のメッシュのインデックスである`other_semi_index`によって指定されます。

結合された境界での2つのメッシュの要素とノードは一致する必要があります。これは現在、[`StructuredMesh`](@ref)に対してのみ実装されています。

# 引数

  * `other_semi_index`: 値がコピーされる半離散化の`SemidiscretizationCoupled`内のインデックス
  * `indices::Tuple`: 別の半離散化のメッシュの境界でのノード/セルインデックス。以下の例を参照してください。
  * `uEltype::Type`: 解の要素タイプ
  * `coupling_converter::CouplingConverter`: 1つのシステムの解状態を別のシステムに変換するために呼び出す関数

# 例

```julia
# メッシュ2の左境界を接続し、私たちの正の境界方向が他の境界の正のy方向と一致するようにします
BoundaryConditionCoupled(2, (:begin, :i), Float64, fun)

# 同じ2つの境界を逆向きに接続します
BoundaryConditionCoupled(2, (:begin, :i_backwards), Float64, fun)

# これをy_neg境界として使用すると、`our_cells[i, 1, j]`が`other_cells[j, end-i, end]`に接続されます
BoundaryConditionCoupled(2, (:j, :i_backwards, :end), Float64, fun)
```

!!! warning "実験的なコード"
    これは実験的な機能であり、いつでも変更される可能性があります。

