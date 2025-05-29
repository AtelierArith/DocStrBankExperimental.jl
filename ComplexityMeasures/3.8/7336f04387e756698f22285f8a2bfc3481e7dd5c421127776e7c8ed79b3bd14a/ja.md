```
RenyiExtropy <: InformationMeasure
RenyiExtropy(; q = 1.0, base = 2)
```

レーニーエントロピー [Liu2023](@cite)。

## 説明

`RenyiExtropy` は [`information`](@ref) と共に使用され、次の式を計算します。

$$
J_R(P) = \dfrac{-(n - 1) \log{(n - 1)} + (n - 1) \log{ \left( \sum_{i=1}^N {(1 - p[i])}^q \right)} }{q - 1}
$$

確率分布 $P = \{p_1, p_2, \ldots, p_N\}$ に対して、与えられた `base` での $\log$ を用います。あるいは、`RenyiExtropy` は [`information_normalized`](@ref) と共に使用することもでき、計算されたエントロピーが最大レーニーエントロピーで正規化されることにより、区間 $[0, 1]$ に収まることを保証します。この最大レーニーエントロピーは次のように与えられます。

$$
J_R(P) = (N - 1)\log \left( \dfrac{n}{n-1} \right) .
$$
