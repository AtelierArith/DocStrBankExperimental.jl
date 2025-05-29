```
ApproximateSignedRankTest(x::AbstractVector{<:Real}[, y::AbstractVector{<:Real}])
```

ウィルコクソン近似符号付き順位U検定を実行し、`x`（または`y`が提供されている場合は`x - y`の差）の分布がゼロの中央値を持つという帰無仮説に対して、中央値がゼロでないという対立仮説を検証します。

p値は符号付き順位統計量の分布に対する正規近似を使用して計算されます：

$$
    \begin{align*}
        μ & = \frac{n(n + 1)}{4}\\
        σ & = \frac{n(n + 1)(2 * n + 1)}{24} - \frac{a}{48}\\
        a & = \sum_{t \in \mathcal{T}} t^3 - t
    \end{align*}
$$

ここで、$\mathcal{T}$は各 tied position での tied values のカウントの集合です。

実装：[`pvalue`](@ref), [`confint`](@ref)
