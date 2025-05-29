```
Correa <: DifferentialInfoEstimator
Correa(definition = Shannon(); m::Int = 1)
```

`Correa`推定量は、[Correa1995](@citet)の方法を使用して、指定された`definition`の`base`で対数を取ることで、時系列の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

`Correa`推定量は、[順序統計](https://en.wikipedia.org/wiki/Order_statistic)に基づく微分エントロピー推定量のクラスに属します。これは*時系列*入力にのみ機能します。

## 説明

連続確率変数$X \in \mathbb{R}$からのサンプル$\bar{X} = \{x_1, x_2, \ldots, x_N \}$があると仮定します。$X$のサポートは$\mathcal{X}$で、密度関数は$f : \mathbb{R} \to \mathbb{R}$です。`Correa`は[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

しかし、上記の積分を直接推定する代わりに、`Correa`は$F$が$X$の分布関数である同等の積分を利用します。

$$
H(X) = \int_0^1 \log \left(\dfrac{d}{dp}F^{-1}(p) \right) dp
$$

この積分は、$\bar{X}$（入力時系列）の[順序統計](https://en.wikipedia.org/wiki/Order_statistic)を最初に計算することによって近似されます。すなわち、$x_{(1)} \leq x_{(2)} \leq \cdots \leq x_{(n)}$であり、端点が含まれることを保証します。`Correa`の[`Shannon`](@ref)微分エントロピーの推定値は次のようになります。

$$
H_C(\bar{X}, m, n) =
\dfrac{1}{n} \sum_{i = 1}^n \log
\left[ \dfrac{ \sum_{j=i-m}^{i+m}(\bar{X}_{(j)} -
\tilde{X}_{(i)})(j - i)}{n \sum_{j=i-m}^{i+m} (\bar{X}_{(j)} - \tilde{X}_{(i)})^2}
\right],
$$

ここで

$$
\tilde{X}_{(i)} = \dfrac{1}{2m + 1} \sum_{j = i - m}^{i + m} X_{(j)}.
$$

さらに、[`information`](@ref)、[`AlizadehArghami`](@ref)、[`Ebrahimi`](@ref)、[`Vasicek`](@ref)、[`DifferentialInfoEstimator`](@ref)も参照してください。
