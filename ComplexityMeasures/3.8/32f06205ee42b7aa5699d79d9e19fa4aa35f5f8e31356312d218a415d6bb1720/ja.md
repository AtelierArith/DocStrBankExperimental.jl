```
Zhu <: DifferentialInfoEstimator
Zhu(; definition = Shannon(), k = 1, w = 0)
```

`Zhu`推定量 [Zhu2015](@cite) は [`KozachenkoLeonenko`](@ref) の拡張であり、定義で指定された`base`の対数を用いて、多次元の[`StateSpaceSet`](@ref)の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

## 説明

連続確率変数 $X \in \mathbb{R}^d$ からのサンプル $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ があり、サポート $\mathcal{X}$ と密度関数 $f : \mathbb{R}^d \to \mathbb{R}$ を持つと仮定します。`Zhu`は[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))]
$$

これは、各点 `xᵢ ∈ x` を囲むハイパーレクタングル内の密度を、`k`最近傍探索を使用して近似することによって行われます。`w`はタイラウィンドウであり、隣接点探索中に時間的隣接点が除外されるかどうかを決定します（デフォルトは`0`で、これは隣接点を探す際に点自体のみが除外されることを意味します）。

関連情報: [`information`](@ref), [`KozachenkoLeonenko`](@ref), [`DifferentialInfoEstimator`](@ref).
