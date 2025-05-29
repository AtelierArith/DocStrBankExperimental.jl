```
V_motifs(A::T; layer::Symbol=:bottom, skipchecks::Bool=false) where {T<:AbstractMatrix}
```

バイアジャシー行列 `A` における V-モチーフの出現回数をその層のためにカウントします。

# 引数

  * `layer`: 層は `layer=:bottom` または `layer=:top` を渡すことで指定できます。層のメンバーシップはグラフの二部マップによって決定されます。
  * `skipchecks`: true の場合、`A` の次元チェックをスキップします。

# 例

```jldoctest V_motifs_bipartite_matrix
julia> A = [1 1; 1 1; 1 0];

julia> V_motifs(A, layer=:bottom)
4

```

```jldoctest V_motifs_bipartite_matrix
julia> V_motifs(A, layer=:top)
2

```
