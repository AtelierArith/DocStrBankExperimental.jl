```
erfinv(x)
```

実数 $x$ の逆誤差関数を計算します。すなわち、

$$
\operatorname{erfinv}(x) = \operatorname{erf}^{-1}(x)
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

外部リンク: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Inverse_functions).

関連: [`erf(x)`](@ref erf).

# 実装

次の文献に掲載されている有理近似を使用します：

> J. M. Blair, C. A. Edwards, and J. H. Johnson, "Rational Chebyshev approximations for the inverse of the error function", Math. Comp. 30, pp. 827–830 (1976). [https://doi.org/10.1090/S0025-5718-1976-0421040-7](https://doi.org/10.1090/S0025-5718-1976-0421040-7), [http://www.jstor.org/stable/2005402](http://www.jstor.org/stable/2005402)


`BigFloat` のニュートン反復と組み合わせて使用します。
