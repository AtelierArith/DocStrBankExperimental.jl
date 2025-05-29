```
Gao <: DifferentialInfoEstimator
Gao(definition = Shannon(); k = 1, w = 0, corrected = true)
```

`Gao`推定量 [Gao2015](@cite) は、[`Shannon`](@ref) 差分 [`information`](@ref) を計算し、[Singh2003](@citet) に基づく `k`-近傍法を使用し、`definition` で指定された `base` の対数を使用します。

`w` は Theiler ウィンドウで、隣接点検索中に時間的隣接点が除外されるかどうかを決定します（デフォルトは `0` で、これは隣接点を検索する際に点自身のみが除外されることを意味します）。

[Gao2015](@citet) はこの推定量の2つのバリアントを提供します。`corrected == false` の場合、未修正バージョンが使用されます。`corrected == true` の場合、修正バージョンが使用され、推定量が漸近的にバイアスがないことが保証されます。

## 説明

連続確率変数 $X \in \mathbb{R}^d$ からのサンプル $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ があると仮定します。サポート $\mathcal{X}$ と密度関数 $f : \mathbb{R}^d \to \mathbb{R}$ を持ちます。`KozachenkoLeonenko` は [`Shannon`](@ref) 差分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$
