```
LocalInteraction{N, T, S, A, TR}
```

N人のプレイヤーを持つローカルインタラクションモデルを表す型です。

# フィールド

  * `players::NTuple{N,Player{2,T}}` : `Player`インスタンスのタプル。
  * `num_actions::Integer` : プレイヤーの行動の数。
  * `adj_matrix::Array{S,2}` : モデル内のグラフの隣接行列。
  * `revision<:AbstractRevision` : 行動プロファイルを修正する方法。
