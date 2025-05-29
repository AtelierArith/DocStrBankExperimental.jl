```
erf(x)
```

$$
x
$$

の誤差関数を計算します。定義は次の通りです。

$$
\operatorname{erf}(x) = \frac{2}{\sqrt{\pi}} \int_0^x \exp(-t^2) \; \mathrm{d}t
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

外部リンク: [DLMF 7.2.1](https://dlmf.nist.gov/7.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

参照: [`erfc(x)`](@ref erfc), [`erfcx(x)`](@ref erfcx), [`erfi(x)`](@ref erfi), [`dawson(x)`](@ref dawson), [`erfinv(x)`](@ref erfinv), [`erfcinv(x)`](@ref erfcinv).

# 実装者

  * `Float32`/`Float64`: C標準数学ライブラリ   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: 多倍精度浮動小数点用Cライブラリ [MPFR](https://www.mpfr.org/)
