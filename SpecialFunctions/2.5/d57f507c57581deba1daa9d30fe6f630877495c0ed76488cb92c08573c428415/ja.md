```
erfi(x)
```

$$
x
$$

の虚数誤差関数を計算します。これは次のように定義されます。

$$
\operatorname{erfi}(x)
= -i \operatorname{erf}(ix)
\quad \text{for} \quad x \in \mathbb{C} \, .
$$

外部リンク: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Imaginary_error_function).

参照: [`erf(x)`](@ref erf).

# 実装者

  * `Float32`/`Float64`: C標準数学ライブラリ   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
