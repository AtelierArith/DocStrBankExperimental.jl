```
Rician(ν, σ)
```

*リシアン分布*は、パラメータ`ν`と`σ`を持ち、確率密度関数は次のようになります：

$$
f(x; \nu, \sigma) = \frac{x}{\sigma^2} \exp\left( \frac{-(x^2 + \nu^2)}{2\sigma^2} \right) I_0\left( \frac{x\nu}{\sigma^2} \right).
$$

形状パラメータとスケールパラメータ`K`と`Ω`が与えられた場合、`ν`と`σ`は次のように計算できます：

$$
\sigma = \sqrt{\frac{\Omega}{2(K + 1)}}, \quad \nu = \sigma\sqrt{2K}
$$

```julia
Rician()         # Rician分布、パラメータν=0およびσ=1
Rician(ν, σ)     # Rician分布、パラメータνおよびσ

params(d)        # パラメータを取得、すなわち(ν, σ)
shape(d)         # 形状パラメータK = ν²/2σ²を取得
scale(d)         # スケールパラメータΩ = ν² + 2σ²を取得
```

外部リンク：

  * [リシアン分布 - Wikipedia](https://en.wikipedia.org/wiki/Rice_distribution)
