```
ExtendedBeta
```

[**拡張ベータ分布**](https://www.vosesoftware.com/riskwiki/Beta4distribution.php)は、形状パラメータ`α`と`β`、およびオプションのサポートパラメータ`min`と`max`を持ち、確率密度関数は次のようになります。

$$
f(x, α, β, \text{min}, \text{max}) =
    \begin{cases}
        0,                                                                                              &\text{if:}~x < \text{min},               \\
        \frac{(x-\text{min})^{α-1} (\text{max}-x)^{β-1}}{B(α,β) (\text{max}-\text{min})^{α+β-1}},  &\text{if:}~\text{min} ≤ x ≤ \text{max}, \\
        0,                                                                                              &\text{if:}~x > max,
    \end{cases}
$$

ここで、B(α,β)はベータ関数です。
