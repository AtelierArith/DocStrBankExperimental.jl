```
EVaR(x̃, α; βmin = 1e-5, βmax = 100, reciprocal = false, distribution = false)
```

確率変数 `x̃` のリスクレベル `α` に対するEVaRリスク測度を計算します（`α` は [0,1] の範囲）。

```
EVaR(values, pmf, α; ...)
```

`values` と確率質量関数 `pmf` を持つ離散確率変数のEVaRを計算します。

`α = 1` のとき、関数は期待値を計算し、`α = 0` のとき、関数は本質的下限（正の確率を持つ最小値）を計算します。

関数は次を解きます

$$
\max_{β ∈ [βmin, βmax]} \operatorname{ERM}_β (x̃) - β^{-1} \log (1/(α)).
$$

大きな値の `βmax` は計算がオーバーフローする原因となる可能性があります。

`reciprocal = false` の場合、上記の準凹問題は直接解かれます。`reciprocal = true` の場合、最適化は `λ = 1/β` の観点から再定式化され、より効率的に解ける（おそらく）凹関数が得られます。

関数は確率空間のすべての要素がゼロでない確率を持つことを暗黙的に仮定しています。

EVaRと、上記の最大値を達成する値 β を返します。

参照: Ahmadi-Javid, A. “Entropic Value-at-Risk: A New Coherent Risk Measure.” Journal of Optimization Theory and Applications 155(3), 2012.
