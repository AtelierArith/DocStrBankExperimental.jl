```
Vasicek <: DifferentialInfoEstimator
Vasicek(definition = Shannon(); m::Int = 1)
```

`Vasicek`推定量は、[Vasicek1976](@citet)の方法を使用して、`definition`で指定された`base`の対数を用いて、時系列の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

`Vasicek`推定量は、[Vasicek1976](@citet)が最初である[順序統計](https://en.wikipedia.org/wiki/Order_statistic)に基づく微分エントロピー推定量のクラスに属します。これは*時系列*入力にのみ機能します。

## 説明

連続確率変数$X \in \mathbb{R}$からのサンプル$\bar{X} = \{x_1, x_2, \ldots, x_N \}$があると仮定します。$X$のサポートは$\mathcal{X}$で、密度関数は$f : \mathbb{R} \to \mathbb{R}$です。`Vasicek`は[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

しかし、上記の積分を直接推定するのではなく、$F$が$X$の分布関数である同等の積分を利用します。

$$
H(X) = \int_0^1 \log \left(\dfrac{d}{dp}F^{-1}(p) \right) dp
$$

この積分は、まず$\bar{X}$（入力時系列）の[順序統計](https://en.wikipedia.org/wiki/Order_statistic)を計算することによって近似されます。すなわち、$x_{(1)} \leq x_{(2)} \leq \cdots \leq x_{(n)}$です。`Vasicek`の[`Shannon`](@ref)微分エントロピー推定値は次のようになります。

$$
\hat{H}_V(\bar{X}, m) =
\dfrac{1}{n}
\sum_{i = 1}^n \log \left[ \dfrac{n}{2m} (\bar{X}_{(i+m)} - \bar{X}_{(i-m)}) \right]
$$

## 使用法

実際には、`m`の選択がエントロピーが真の値に収束する速さに影響を与えます。`m`の小さい値では収束が遅いため、`m`を時系列の長さ`n`に応じてスケーリングし、`m >= n/100`を使用することをお勧めします（これはこのパッケージのテストに基づくヒューリスティックです）。

関連情報: [`information`](@ref), [`Correa`](@ref), [`AlizadehArghami`](@ref), [`Ebrahimi`](@ref), [`DifferentialInfoEstimator`](@ref).
