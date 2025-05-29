```
initialstate(m::Union{POMDP,MDP})
```

(PO)MDP `m` の初期状態の分布を返します。

確率密度または質量関数を明示的に定義するのが難しい場合は、サンプリングのためのモデルを定義するために `POMDPModelTools.ImplicitDistribution` を使用することを検討してください。
