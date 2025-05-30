```
erfc(x)
```

$$
x
$$

の補完誤差関数を計算します。定義は次の通りです。

$$
\operatorname{erfc}(x)
= 1 - \operatorname{erf}(x)
= \frac{2}{\sqrt{\pi}} \int_x^\infty \exp(-t^2) \; \mathrm{d}t
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

これは大きな$x$に対する`1-erf(x)`の正確なバージョンです。

外部リンク: [DLMF 7.2.2](https://dlmf.nist.gov/7.2.2), [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Complementary_error_function).

参照: [`erf(x)`](@ref erf).

# 実装者

  * `Float32`/`Float64`: C標準数学ライブラリ   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: 多倍精度浮動小数点用Cライブラリ [MPFR](https://www.mpfr.org/)
