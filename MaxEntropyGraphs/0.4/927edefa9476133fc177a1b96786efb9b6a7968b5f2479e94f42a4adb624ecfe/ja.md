```
V_motifs(m::BiCM, i::Int, j::Int; layer::Symbol=:bottom, precomputed::Bool=false)
```

BiCM `m` のノード `i` と `j` の間の `layer` における期待される V-モチーフの出現回数をカウントします。

# 引数

  * `layer`: レイヤーは `layer=:bottom` または `layer=:top` を渡すことで指定できます。
  * `precomputed`: true の場合、二部隣接行列の期待値が使用され、それ以外の場合はモデルパラメータから計算されます。

*注意*: レイヤーに応じて、タプル (`i`, `j`) は期待される二部隣接行列 `A` の行 (:bottom) または列 (:top) を示します。

# 例

```jldoctest V_motifs_bicm_local
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> V_motifs(model, 16, 13, layer=:bottom), V_motifs(model, 16, 13, layer=:bottom, precomputed=false)
(3.385652998856112, 3.3856529988561115)

```

```jldoctest V_motifs_bicm_local
julia> V_motifs(model, 5, 1, layer=:top), V_motifs(model, 5, 1, layer=:top, precomputed=false)
(9.46988024296453, 9.469880242964528)

```
