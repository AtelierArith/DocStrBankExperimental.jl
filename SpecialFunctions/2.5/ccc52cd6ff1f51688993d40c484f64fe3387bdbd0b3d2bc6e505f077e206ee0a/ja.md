```
sinint(x)
```

$$
x
$$

の正弦積分関数を計算します。これは次のように定義されます。

$$
\operatorname{Si}(x)
:= \int_0^x \frac{\sin t}{t} \, \mathrm{d}t
\quad \text{for} \quad
x \in \mathbb{R} \,.
$$

外部リンク: [DLMF 6.2.9](https://dlmf.nist.gov/6.2.9), [Wikipedia](https://en.wikipedia.org/wiki/Trigonometric_integral#Sine_integral).

関連項目: [`cosint(x)`](@ref SpecialFunctions.cosint).

# 実装

[DLMF 6.2.9](https://dlmf.nist.gov/6.2.9)に記載されている有理近似を使用します。

注: $\text{Ci}(x)$の2番目のゼロには誤植があり、修正されました: 記事では$r_1 = 3.38418 0422\mathbf{8} 51186 42639 78511 46402$となっていますが、実際には$r_1 = 3.38418 0422\mathbf{5} 51186 42639 78511 46402$です。
