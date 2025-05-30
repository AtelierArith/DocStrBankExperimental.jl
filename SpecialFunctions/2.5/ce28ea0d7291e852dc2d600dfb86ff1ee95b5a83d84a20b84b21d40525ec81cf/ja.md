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

[MacLeod (1996)](@cite macleod_1996)に掲載された有理近似を使用します。

注: $\text{Ci}(x)$の2番目のゼロには誤植があり、修正されています: 記事では$r_1 = 3.38418 0422\mathbf{8} 51186 42639 78511 46402$となっていますが、実際には$r_1 = 3.38418 0422\mathbf{5} 51186 42639 78511 46402$です。
