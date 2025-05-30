```
FourierFilterNet(in_dims::Int, out_dims::Int; hidden_dims::Int, num_layers::Int,
                 bandwidth::Real)
```

乗法フィルタネットワークは次のように定義されます。

$$
\begin{aligned}
z^{(1)} &=g\left(x ; \theta^{(1)}\right) \\
z^{(i+1)} &=\left(W^{(i)} z^{(i)}+b^{(i)}\right) \circ \sin \left(\omega^{(i)} x+\phi^{(i)}\right)\right) \\
f(x) &=W^{(k)} z^{(k)}+b^{(k)}
\end{aligned}
$$

## キーワード引数

  * `bandwidth`: ネットワークの最大帯域幅。帯域幅は各フィルタの帯域幅の合計です。

## パラメータ

  * フィルタのパラメータ：

$$
    W\sim \mathcal{U}(-\frac{ω}{n}, \frac{ω}{n}), \quad b\sim \mathcal{U}(-\pi, \pi),
$$

ここで `n` はフィルタの数です。

周期 $P$ の周期関数に対して、振幅-位相形式のフーリエ級数は次のようになります。

$$
s_N(x)=\frac{a_0}{2}+\sum_{n=1}^N{a_n}\cdot \sin \left( \frac{2\pi}{P}nx+\varphi _n \right)
$$

帯域幅とモデルのパラメータの間には次の関係があります：

$$
ω = 2πB=\frac{2πN}{P}.
$$

ここで $B$ はネットワークの帯域幅です。

## 参考文献

[fathony2021multiplicative](@cite)

[lindell2021bacon](@cite) ```
