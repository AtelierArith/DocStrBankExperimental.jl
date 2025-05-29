```
V_motifs(B::T, i::Int, j::Int; layer::Symbol=:bottom, skipchecks::Bool=false) where {T<:AbstractMatrix}
```

バイアダジェンシー行列 `B` におけるノード `i` と `j` の間の V-モチーフの出現回数をカウントします。

# 引数

  * `layer`: レイヤーは `layer=:bottom` または `layer=:top` を渡すことで指定できます。
  * `skipchecks`: true の場合、`B` の次元チェックをスキップします。

*注意*: レイヤーに応じて、タプル (`i`, `j`) はバイアダジェンシー行列 `B` の行 (:bottom) または列 (:top) を示します。

# 例

```jldoctest V_motifs_bipartite_matrix_local
julia> B = [1 1; 1 1; 1 0];

julia> V_motifs(B, 1, 2, layer=:bottom)
2

```

```jldoctest V_motifs_bipartite_matrix_local
julia> V_motifs(B, 1, 2, layer=:top)
2

```
