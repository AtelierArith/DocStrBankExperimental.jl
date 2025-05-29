```
TsallisExtropy <: InformationMeasure
TsallisExtropy(; base = 2)
```

Tsallisエントロピー [Xue2023](@cite)。

## 説明

`TsallisExtropy`は[`information`](@ref)と共に使用され、次の式を計算します。

$$
J_T(P) = k \dfrac{N - 1 - \sum_{i=1}^N ( 1 - p[i])^q}{q - 1}
$$

確率分布$P = \{p_1, p_2, \ldots, p_N\}$に対して、指定された`base`での$\log$を用います。あるいは、`TsallisExtropy`は[`information_normalized`](@ref)と共に使用することもでき、計算されたエントロピーが最大のTsallisエントロピーで正規化されることにより、区間$[0, 1]$に収まることを保証します。この最大のTsallisエントロピーは次のように与えられます。

$$
J_T(P) = \dfrac{(N - 1)N^{q - 1} - (N - 1)^q}{(q - 1)N^{q - 1}}
$$
