```
LogitDynamics{N, T, S}
```

Logit-Dynamicsモデルを表す型。

# フィールド

  * `players::NTuple{N,Player{N,T}}` : `Player`インスタンスのタプル。
  * `nums_actions::NTuple{N,Int}` : 各プレイヤーのためのアクションの数のタプル。
  * `beta<:Real` : プレイヤーの決定におけるノイズのレベル。
  * `choice_probs::Vector{Array}` : 各アクションの選択確率、各プレイヤーごとに1つ。
