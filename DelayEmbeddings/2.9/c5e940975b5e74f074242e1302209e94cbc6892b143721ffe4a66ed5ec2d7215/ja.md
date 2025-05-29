```
exponential_decay_fit(x, y, weight = :equal) -> τ
```

`y = exp(-x/τ)`の形の最小二乗フィットを行い、`τ`を返します。出典:  http://mathworld.wolfram.com/LeastSquaresFittingExponential.html。`x`と`y`の長さが等しく、`y ≥ 0`であることを前提としています。

`y`の小さい値により重みを与えるメソッドを使用するには、`weight = :small`を指定してください。
