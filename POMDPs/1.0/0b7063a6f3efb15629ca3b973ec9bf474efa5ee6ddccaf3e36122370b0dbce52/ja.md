```
initialobs(m::POMDP, s)
```

POMDP `m` と状態 `s` の初期観測の分布を返します。

確率密度または質量関数を明示的に定義するのが難しい場合は、`POMDPModelTools.ImplicitDistribution` を使用してサンプリングのためのモデルを定義することを検討してください。

この関数は、ポリシーが初期信念ではなく初期観測を期待する場合、例えば強化学習の設定でのみ使用されます。標準的なPOMDPシミュレーションでは使用されません。
