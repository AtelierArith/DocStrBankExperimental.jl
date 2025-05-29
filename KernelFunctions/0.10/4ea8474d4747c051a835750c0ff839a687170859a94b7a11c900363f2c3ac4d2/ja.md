```
NeuralNetworkKernel()
```

単一の隠れ層を持つベイジアンニューラルネットワークのユニット数が無限大に近づくときの限界として得られるガウス過程のカーネル。

# 定義

次のように定義された $h$ 隠れユニットを持つ単層ベイジアンニューラルネットワーク $f \colon \mathbb{R}^d \to \mathbb{R}$ を考えます。

$$
f(x; b, v, u) = b + \sqrt{\frac{\pi}{2}} \sum_{i=1}^{h} v_i \mathrm{erf}\big(u_i^\top x\big),
$$

ここで、$\mathrm{erf}$ は誤差関数であり、事前分布は次のように与えられます。

$$
\begin{aligned}
b &\sim \mathcal{N}(0, \sigma_b^2),\\
v &\sim \mathcal{N}(0, \sigma_v^2 \mathrm{I}_{h}/h),\\
u_i &\sim \mathcal{N}(0, \mathrm{I}_{d}/2) \qquad (i = 1,\ldots,h).
\end{aligned}
$$

$$
h \to \infty
$$

のとき、ニューラルネットワークはガウス過程に収束します。

$$
g(\cdot) \sim \mathcal{GP}\big(0, \sigma_b^2 + \sigma_v^2 k(\cdot, \cdot)\big),
$$

ここで、ニューラルネットワークカーネル $k$ は次のように与えられます。

$$
k(x, x') = \arcsin\left(\frac{x^\top x'}{\sqrt{\big(1 + \|x\|^2_2\big) \big(1 + \|x'\|_2^2\big)}}\right)
$$

入力 $x, x' \in \mathbb{R}^d$ に対して。[^\text{CW}]

[^CW]: C. K. I. Williams (1998). Computation with infinite neural networks.
