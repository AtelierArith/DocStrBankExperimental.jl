```
profile(m::LinearMixedModel; threshold = 4)
```

`m` に対する固定効果係数の目的のための `MixedModelProfile` を返します。

`m` は `!isfitted(m)` の場合 `refit!` です。

プロファイリングはパラメータ推定値から始まり、パラメータの境界に達するか、ζ の絶対値が `threshold` を超えるまで続きます。
