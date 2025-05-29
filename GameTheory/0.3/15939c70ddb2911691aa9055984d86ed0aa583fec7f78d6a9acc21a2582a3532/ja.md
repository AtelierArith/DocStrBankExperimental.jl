```
NormalFormGame([T=Float64], nums_actions)
```

N人プレイヤーのNormalFormGameのコンストラクタで、すべてのペイオフが0で構成されています。

# 引数

  * `T::Type` : ペイオフ値の型; 指定されていない場合はデフォルトで`Float64`になります。
  * `nums_actions::NTuple{N,Int}` : N人のプレイヤーのアクションの数。
