```
KozachenkoLeonenko <: DifferentialInfoEstimator
KozachenkoLeonenko(definition = Shannon(); w::Int = 0)
```

`KozachenkoLeonenko`推定量[KozachenkoLeonenko1987](@cite)は、`definition`で指定された`base`の対数を用いて、多次元[`StateSpaceSet`](@ref)の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

## 説明

連続確率変数$X \in \mathbb{R}^d$からのサンプル$\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$があり、サポート$\mathcal{X}$と密度関数$f : \mathbb{R}^d \to \mathbb{R}$があると仮定します。`KozachenkoLeonenko`は、[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))]
$$

これは、[KozachenkoLeonenko1987](@citet)で説明されている最近傍法を使用して推定されます。[Charzyńska2015](@citet)で説明されています。

`w`はTheilerウィンドウで、隣接点検索中に時間的隣接点が除外されるかどうかを決定します（デフォルトは`0`で、隣接点を検索する際に点自体のみが除外されます）。

[`Kraskov`](@ref)とは対照的に、この推定量は*最も近い*隣接点のみを使用します。

関連情報: [`information`](@ref), [`Kraskov`](@ref), [`DifferentialInfoEstimator`](@ref).
