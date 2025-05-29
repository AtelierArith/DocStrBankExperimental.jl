```
on_states(onstates, G, R, S, insertstep)
on_states(G::Int, R, S, insertstep)
on_states(onstates::Vector, G, R, S)
```

GRおよびGRSモデルのオンステートインデックスのベクトルを返します。

# 説明

この関数は、GRおよびGRSモデルのオンステートインデックスのベクトルを返します。空の`onstates`と非空の`onstates`の両方を処理できます。

# 引数

  * `onstates`: 初期オンステート。整数のベクトルまたは空であることができます。
  * `G::Int`: 遺伝子の総数。
  * `R`: レポータの数。
  * `S`: ステートの数。
  * `insertstep`: 挿入ステップ。

# メソッド

  * `on_states(onstates, G, R, S, insertstep)`: 空の`onstates`と非空の`onstates`の両方を処理します。
  * `on_states(G::Int, R, S, insertstep)`: `onstates`をゼロから生成します。
  * `on_states(onstates::Vector, G, R, S)`: 提供されたベクトルに基づいて`onstates`を生成します。

# 戻り値

  * `Vector{Int}`: 新しいオンステートのベクトル。
