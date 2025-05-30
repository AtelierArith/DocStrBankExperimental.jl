```
dawson(x)
```

Dawson関数（スケーリングされた虚数誤差関数）を$x$について計算します。定義は次の通りです。

$$
\operatorname{dawson}(x)
= \frac{\sqrt{\pi}}{2} e^{-x^2} \operatorname{erfi}(x)
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

これは、大きな$x$に対する$\frac{\sqrt{\pi}}{2} e^{-x^2} \operatorname{erfi}(x)$の正確なバージョンです。

外部リンク: [DLMF 7.2.5](https://dlmf.nist.gov/7.2.5), [Wikipedia](https://en.wikipedia.org/wiki/Dawson_function).

参照: [`erfi(x)`](@ref erfi).

# 実装者

  * `Float32`/`Float64`: C標準数学ライブラリ   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
