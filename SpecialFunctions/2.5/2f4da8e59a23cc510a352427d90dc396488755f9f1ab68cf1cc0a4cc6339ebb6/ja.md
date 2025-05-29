```
erfcx(x)
```

スケーリングされた補完誤差関数 $x$ を計算します。定義は次の通りです。

$$
\operatorname{erfcx}(x)
= e^{x^2} \operatorname{erfc}(x)
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

これは大きな $x$ に対する $e^{x^2} \operatorname{erfc}(x)$ の正確なバージョンです。また、$\operatorname{erfcx}(-ix)$ は Faddeeva 関数 `w(x)` を計算することにも注意してください。

外部リンク: [DLMF 7.2.3](https://dlmf.nist.gov/7.2.3), [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Complementary_error_function).

参照: [`erfc(x)`](@ref erfc).

# 実装者

  * `Float32`/`Float64`: C 標準数学ライブラリ   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: MPFR はこの関数のオープンな TODO アイテムがあります。それまでは、尾部のために   [DLMF 7.12.1](https://dlmf.nist.gov/7.12.1) を使用します。
