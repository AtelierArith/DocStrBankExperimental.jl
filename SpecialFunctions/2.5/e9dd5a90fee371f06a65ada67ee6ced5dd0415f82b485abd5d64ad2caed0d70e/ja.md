```
erfinv(x)
```

実数 $x$ の逆誤差関数を計算します。すなわち、

$$
\operatorname{erfinv}(x) = \operatorname{erf}^{-1}(x)
\quad \text{for} \quad x \in \mathbb{R} \, .
$$

外部リンク: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Inverse_functions)。

関連: [`erf(x)`](@ref erf)。

# 実装

[Blair (1976)](@cite blair_1976) に表された有理近似を使用し、`BigFloat` のニュートン反復を組み合わせます。
