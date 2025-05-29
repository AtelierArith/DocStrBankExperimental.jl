```
AlizadehArghami <: DifferentialInfoEstimator
AlizadehArghami(definition = Shannon(); m::Int = 1)
```

`AlizadehArghami`推定量は、[Alizadeh2010](@citet)の方法を使用して、`definition`で指定された`base`の対数を用いて、時系列の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

`AlizadehArghami`推定量は、[順序統計](https://en.wikipedia.org/wiki/Order_statistic)に基づく微分エントロピー推定量のクラスに属します。これは*時系列*入力にのみ機能します。

## 説明

連続確率変数$X \in \mathbb{R}$からのサンプル$\bar{X} = \{x_1, x_2, \ldots, x_N \}$があり、サポート$\mathcal{X}$と密度関数$f : \mathbb{R} \to \mathbb{R}$があると仮定します。`AlizadehArghami`は、[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

しかし、上記の積分を直接推定する代わりに、$F$が$X$の分布関数である同等の積分を利用します：

$$
H(X) = \int_0^1 \log \left(\dfrac{d}{dp}F^{-1}(p) \right) dp.
$$

この積分は、まず$\bar{X}$（入力時系列）の[順序統計](https://en.wikipedia.org/wiki/Order_statistic)を計算することによって近似されます。すなわち、$x_{(1)} \leq x_{(2)} \leq \cdots \leq x_{(n)}$です。`AlizadehArghami`の[`Shannon`](@ref)微分エントロピー推定は、[`Vasicek`](@ref)推定$\hat{H}_{V}(\bar{X}, m, n)$に修正係数を加えたものです。

$$
\hat{H}_{A}(\bar{X}, m, n) = \hat{H}_{V}(\bar{X}, m, n) +
\dfrac{2}{n}\left(m \log(2) \right).
$$

参照：[`information`](@ref), [`Correa`](@ref), [`Ebrahimi`](@ref), [`Vasicek`](@ref), [`DifferentialInfoEstimator`](@ref).
