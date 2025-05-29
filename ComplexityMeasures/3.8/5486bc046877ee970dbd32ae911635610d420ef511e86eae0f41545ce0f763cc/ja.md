```
Goria <: DifferentialInfoEstimator
Goria(measure = Shannon(); k = 1, w = 0)
```

`Goria`推定量[Goria2005](@cite)は、指定された`base`の対数を用いて、多次元[`StateSpaceSet`](@ref)の[`Shannon`](@ref)微分[`information`](@ref)を計算します。

## 説明

連続確率変数$X \in \mathbb{R}^d$からのサンプル$\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$があり、サポート$\mathcal{X}$と密度関数$f : \mathbb{R}^d \to \mathbb{R}$を持つと仮定します。`Goria`は[`Shannon`](@ref)微分エントロピーを推定します。

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

具体的には、$\bf{n}_1, \bf{n}_2, \ldots, \bf{n}_N$をサンプル$\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$の`k`-th最近傍までの距離とします。次に、距離の幾何平均を次のように定義します。

$$
\hat{\rho}_k = \left( \prod_{i=1}^N \right)^{\dfrac{1}{N}}
$$

[Goria2005](@citet)のShannon微分エントロピーの推定値は次のようになります。

$$
\hat{H} = m\hat{\rho}_k + \log(N - 1) - \psi(k) + \log c_1(m),
$$

ここで$c_1(m) = \dfrac{2\pi^\frac{m}{2}}{m \Gamma(m/2)}$であり、$\psi$はディガンマ関数です。
