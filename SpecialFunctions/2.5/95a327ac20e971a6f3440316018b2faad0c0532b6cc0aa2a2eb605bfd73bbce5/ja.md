```
cosint(x)
```

$$
x
$$

のコサイン積分関数を計算します。定義は次の通りです。

$$
\operatorname{Ci}(x)
:= \gamma + \log x + \int_0^x \frac{\cos (t) - 1}{t} \, \mathrm{d}t
\quad \text{for} \quad
x > 0 \,,
$$

ここで、$\gamma$はオイラー・マスケローニ定数です。

外部リンク: [DLMF 6.2.13](https://dlmf.nist.gov/6.2.13), [Wikipedia](https://en.wikipedia.org/wiki/Trigonometric_integral#Cosine_integral).

参照: [`sinint(x)`](@ref SpecialFunctions.sinint).

# 実装

次の文献に掲載されている有理近似を使用します。

> A.J. MacLeod, "Rational approximations, software and test methods for sine and cosine integrals", Numer. Algor. 12, pp. 259–272 (1996). [https://doi.org/10.1007/BF02142806](https://doi.org/10.1007/BF02142806), [https://link.springer.com/article/10.1007/BF02142806](https://link.springer.com/article/10.1007/BF02142806).


注意: $\text{Ci}(x)$の2番目のゼロには誤植があり、修正されています: 記事では$r_1 = 3.38418 0422\mathbf{8} 51186 42639 78511 46402$となっていますが、実際には$r_1 = 3.38418 0422\mathbf{5} 51186 42639 78511 46402$です。
