```
NormalFormGame{N,T}
```

N人の通常形ゲームを表す型。

# フィールド

  * `players::NTuple{N,Player{N,T<:Real}}` : プレイヤーインスタンスのタプル。
  * `nums_actions::NTuple{N,Int}` : 各プレイヤーのためのアクションの数のタプル。
