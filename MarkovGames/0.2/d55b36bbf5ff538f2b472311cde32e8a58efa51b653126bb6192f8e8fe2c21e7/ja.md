```
transition(m::Game, state, action)
```

現在の状態-共同アクションペアからの遷移分布を返します。確率密度または質量関数を明示的に定義するのが難しい場合は、`POMDPModelTools.ImplicitDistribution`を使用して生成モデルを定義することを検討してください。
