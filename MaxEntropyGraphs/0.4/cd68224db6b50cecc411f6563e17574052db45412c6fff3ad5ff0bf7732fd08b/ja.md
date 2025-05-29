```
V_motifs(m::BiCM; layer::Symbol=:bottom)
```

BiCM `m` の特定のレイヤーにおける V-モチーフの出現回数をカウントします。

# 引数

  * `layer`: レイヤーは `layer=:bottom` または `layer=:top` を渡すことで指定できます。レイヤーの所属はグラフの二部マップによって決定されます。
  * `precomputed`: true の場合、二部隣接行列の期待値が使用され、それ以外の場合はモデルパラメータからパラメータが計算されます。

# 例

```jldoctest V_motifs_bicm
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> V_motifs(model, layer=:bottom), V_motifs(model, layer=:bottom, precomputed=false)
(449.2569925909879, 449.2569925909879)

```

```jldoctest V_motifs_bicm
julia> V_motifs(model, layer=:top), V_motifs(model, layer=:top, precomputed=false)
(180.2569926636081, 180.2569926636081)
```
