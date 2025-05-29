```
StochasticFictitiousPlay{N, T, TG, TD}
```

N人のプレイヤーを持つ確率的虚構プレイモデルを表す型です。

# フィールド

  * `players::NTuple{N,Player{N,T}}` : `Player` インスタンスのタプル。
  * `nums_actions::NTuple{N,Int}` : 各プレイヤーのためのアクションの数のタプル。
  * `gain::TG<:AbstractGain` : 利得の型。
  * `d::TD<:Distributions.Distribution` : 利得の摂動が引き出される `Distribution` インスタンス。
