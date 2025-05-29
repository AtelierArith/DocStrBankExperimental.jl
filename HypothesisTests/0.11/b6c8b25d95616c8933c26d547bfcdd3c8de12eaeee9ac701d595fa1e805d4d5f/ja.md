```
ApproximateMannWhitneyUTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

`x`と`y`の同じ母集団から抽出された観測値のうち、`x`から抽出された観測値が`y`から抽出された観測値より大きい確率が、`y`から抽出された観測値が`x`から抽出された観測値より大きい確率と等しいという帰無仮説に対して、これらの確率が等しくないという対立仮説を検定する近似的なマン・ホイットニーU検定を実行します。

p値はマン・ホイットニーU統計量の分布に対する正規近似を使用して計算されます：

$$
    \begin{align*}
        μ & = \frac{n_x n_y}{2}\\
        σ & = \frac{n_x n_y}{12}\left(n_x + n_y + 1 - \frac{a}{(n_x + n_y)(n_x +
            n_y - 1)}\right)\\
        a & = \sum_{t \in \mathcal{T}} t^3 - t
    \end{align*}
$$

ここで、$\mathcal{T}$は各 tied position での tied values のカウントの集合です。

実装: [`pvalue`](@ref) ```
