```
FrontLastPenalty(SimpleChain, frontpen(λ₁...), lastpen(λ₂...))
```

`frontpen`を最後のレイヤーを除くすべてのレイヤーに適用し、代わりに最後のレイヤーに`lastpen`を適用します。ここでの「最後のレイヤー」は損失関数を無視します。つまり、チェーンの最後の要素が損失レイヤーである場合、`lastpen`はこの前のレイヤーに適用されます。
