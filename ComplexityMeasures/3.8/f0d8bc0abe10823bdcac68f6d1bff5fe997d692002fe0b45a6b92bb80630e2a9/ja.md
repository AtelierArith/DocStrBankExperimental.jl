```
GeneralizedSchuermann <: DiscreteInfoEstimatorShannon
GeneralizedSchuermann(definition = Shannon(); a = 1.0)
```

`GeneralizedSchuermann`推定量は、[情報](@ref)と共に使用され、[Grassberger2022](@citet)で示されたバイアス補正された推定量を用いて離散の[`Shannon`](@ref)エントロピーを計算します。

名前の「一般化された」部分は、異なる結果に対して異なるパラメータ$a_i$を選択できる可能性に起因しています。[Schurmann2004](@citet)推定量（[`Schuermann`](@ref)）とは異なります。異なる結果に異なるパラメータが割り当てられる場合、`a`は`length(outcomes)`の長さのパラメータのベクトルでなければなりません。結果は[`outcomes`](@ref)を使用して取得されます。詳細については[Grassberger2022](@citet)を参照してください。`a`が実数の場合、$a_i = a \forall i$となり、推定量は[`Schuermann`](@ref)推定量に簡約されます。

## 説明

$$
M
$$

の結果に対する$N$の観測値のセットに対して、推定量は次のように与えられます。

$$
H_S^{opt} = \varphi(N) - \dfrac{1}{N} \sum_{i=1}^M n_i G_{n_i}(a_i),
$$

ここで、$n_i$はi番目の結果の観測頻度です。

$$
G_n(a) = \varphi(n) + (-1)^n \int_0^a \dfrac{x^{n - 1}}{x + 1} dx,
$$

$$
G_n(1) = G_n
$$

および$G_n(0) = \varphi(n)$、そして

$$
G_n = \varphi(n) + (-1)^n \int_0^1 \dfrac{x^{n - 1}}{x + 1} dx.
$$
