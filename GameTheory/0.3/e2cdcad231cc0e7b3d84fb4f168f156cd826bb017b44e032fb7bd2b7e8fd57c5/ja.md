```
FictitiousPlay{N, T, TG}
```

N人のプレイヤーを持つフィクティシャスプレイモデルを表す型です。

# フィールド

  * `players::NTuple{N,Player{N,T}}` : `Player`インスタンスのタプル。
  * `nums_actions::NTuple{N,Int}` : 各プレイヤーのためのアクションの数のタプル。
  * `gain::TG<:AbstractGain` : ゲインタイプ。
