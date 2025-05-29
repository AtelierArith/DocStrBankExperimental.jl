```
ERM(x̃, β [, x̃min, check_inputs = true])
```

確率変数 `x̃` のエントロピーリスク測度をリスクレベル `β` で計算します。

オプションの `x̃min` パラメータは、指数関数を計算する際のオーバーフローを避けるためのオフセットとして使用されます。指定されていない場合は、代わりに `x̃` の最小値が使用されます。

最大化問題を仮定します。 `β=0` を使用すると期待値が計算され、 `β=Inf` を使用すると本質的下限（正の確率を持つ最小値）が計算されます。

詳細については、[https://en.wikipedia.org/wiki/Entropic*risk*measure](https://en.wikipedia.org/wiki/Entropic_risk_measure) を参照してください。
