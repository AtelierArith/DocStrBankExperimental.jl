```
Kraskov <: DifferentialInfoEstimator
Kraskov(definition = Shannon(); k::Int = 1, w::Int = 0)
```

`Kraskov`推定量は、[`Shannon`](@ref)微分[`information`](@ref)を、[Kraskov2004](@citet)の`k`-近傍探索法を使用して、`StateSpaceSet`(@ref)の多次元空間から計算します。対数は`definition`で指定された`base`に基づいています。

`w`はTheilerウィンドウで、近傍探索中に時間的近傍が除外されるかどうかを決定します（デフォルトは`0`で、これは近傍を探す際に点自体のみが除外されることを意味します）。

## 説明

連続確率変数$X \in \mathbb{R}^d$からのサンプル$\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$があり、サポート$\mathcal{X}$と密度関数$f : \mathbb{R}^d \to \mathbb{R}$を持つと仮定します。`Kraskov`は[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

関連情報: [`information`](@ref), [`KozachenkoLeonenko`](@ref), [`DifferentialInfoEstimator`](@ref).
