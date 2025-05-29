```
transition(m::POMDP, state, action)
transition(m::MDP, state, action)
```

現在の状態-行動ペアからの遷移分布を返します。

確率密度または質量関数を明示的に定義することが難しい場合は、`POMDPModelTools.ImplicitDistribution`を使用して生成モデルを定義することを検討してください。
