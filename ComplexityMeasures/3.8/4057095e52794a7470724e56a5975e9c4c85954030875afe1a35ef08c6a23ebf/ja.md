```
Tsallis <: InformationMeasure
Tsallis(q; k = 1.0, base = 2)
Tsallis(; q = 1.0, k = 1.0, base = 2)
```

Tsallisの一般化された順序`q`エントロピー [Tsallis1988](@cite) は、エントロピーを計算するために[`information`](@ref)と共に使用されます。

`base`は、Tsallisエントロピーが[`Shannon`](@ref)エントロピーに還元される制限ケース`q == 1`にのみ適用されます。

## 説明

Tsallisエントロピーは、ボルツマン-ギブスエントロピーの一般化であり、`k`はボルツマン定数を表します。これは次のように定義されます。

$$
S_q(p) = \frac{k}{q - 1}\left(1 - \sum_{i} p[i]^q\right)
$$

Tsallisエントロピーの最大値は $k(L^{1 - q} - 1)/(1 - q)$ であり、ここで $L$ は[`total_outcomes`](@ref)です。
