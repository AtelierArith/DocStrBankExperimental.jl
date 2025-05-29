```
Ebrahimi <: DifferentialInfoEstimator
Ebrahimi(definition = Shannon(); m::Int = 1)
```

`Ebrahimi`推定量は、[Ebrahimi1994](@citet)の方法を使用して、`definition`で指定された`base`の対数を用いて、時系列の[`Shannon`](@ref) [`information`](@ref)を計算します。

`Ebrahimi`推定量は、[順序統計](https://en.wikipedia.org/wiki/Order_statistic)に基づく微分エントロピー推定量のクラスに属します。これは*時系列*入力にのみ機能します。

## 説明

連続確率変数$X \in \mathbb{R}$からのサンプル$\bar{X} = \{x_1, x_2, \ldots, x_N \}$があると仮定します。$X$のサポートは$\mathcal{X}$で、密度関数は$f : \mathbb{R} \to \mathbb{R}$です。`Ebrahimi`は、[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

しかし、上記の積分を直接推定するのではなく、$F$が$X$の分布関数である同等の積分を利用します。

$$
H(X) = \int_0^1 \log \left(\dfrac{d}{dp}F^{-1}(p) \right) dp
$$

この積分は、まず$\bar{X}$（入力時系列）の[順序統計](https://en.wikipedia.org/wiki/Order_statistic)を計算することによって近似されます。すなわち、$x_{(1)} \leq x_{(2)} \leq \cdots \leq x_{(n)}$です。`Ebrahimi`の[`Shannon`](@ref)微分エントロピー推定値は次のようになります。

$$
\hat{H}_{E}(\bar{X}, m) =
\dfrac{1}{n} \sum_{i = 1}^n \log
\left[ \dfrac{n}{c_i m} (\bar{X}_{(i+m)} - \bar{X}_{(i-m)}) \right],
$$

ここで

$$
c_i =
\begin{cases}
    1 + \frac{i - 1}{m}, & 1 \geq i \geq m \\
    2,                    & m + 1 \geq i \geq n - m \\
    1 + \frac{n - i}{m} & n - m + 1 \geq i \geq n
\end{cases}.
$$

また、[`information`](@ref)、[`Correa`](@ref)、[`AlizadehArghami`](@ref)、[`Vasicek`](@ref)、[`DifferentialInfoEstimator`](@ref)も参照してください。
