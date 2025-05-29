```
ZhuSingh <: DifferentialInfoEstimator
ZhuSingh(definition = Shannon(); k = 1, w = 0)
```

`ZhuSingh`推定量 [Zhu2015](@cite) は、定義で指定された`base`の対数を用いて、多次元[`StateSpaceSet`](@ref)の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

## 説明

連続確率変数$X \in \mathbb{R}^d$からのサンプル$\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$があり、サポート$\mathcal{X}$と密度関数$f : \mathbb{R}^d \to \mathbb{R}$があると仮定します。`ZhuSingh`は[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

[`Zhu`](@ref)と同様に、この推定量は、各点`xᵢ ∈ x`を囲むハイパーレクタングル内の確率を`k`近傍探索を使用して近似します。しかし、これらのハイパーレクタングルの境界に落ちる隣接点の数も考慮します。この推定量は、[Singh2003](@citet)のエントロピー推定量の拡張です。

`w`はタイラーウィンドウで、隣接点探索中に時間的隣接点が除外されるかどうかを決定します（デフォルトは`0`で、これは隣接点を探す際に点自体のみが除外されることを意味します）。

参照: [`information`](@ref), [`DifferentialInfoEstimator`](@ref).
