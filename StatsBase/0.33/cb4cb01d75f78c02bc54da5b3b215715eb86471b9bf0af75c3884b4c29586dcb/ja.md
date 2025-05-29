```
cronbachalpha(covmatrix::AbstractMatrix{<:Real})
```

共分散行列 `covmatrix` から Cronbach のアルファ (1951) を計算します。 [公式](https://en.wikipedia.org/wiki/Cronbach%27s_alpha) に従います：

$$
\rho = \frac{k}{k-1} (1 - \frac{\sum^k_{i=1} \sigma^2_i}{\sum_{i=1}^k \sum_{j=1}^k \sigma_{ij}})
$$

ここで、$k$ は項目の数、すなわち列の数、$\sigma_i^2$ は項目の分散、$\sigma_{ij}$ は項目間の共分散です。

`CronbachAlpha` オブジェクトを返し、以下を保持します：

  * `alpha`: `covmatrix` のすべての項目、すなわち列に対する Cronbach のアルファスコア；および
  * `dropped`: 特定の項目、すなわち列が `covmatrix` から削除された場合の Cronbach のアルファスコアを示すベクトル。

# 例

```jldoctest
julia> using StatsBase

julia> cov_X = [10 6 6 6;
                6 11 6 6;
                6 6 12 6;
                6 6 6 13];

julia> cronbachalpha(cov_X)
Cronbach's alpha for all items: 0.8136

Cronbach's alpha if an item is dropped:
item 1: 0.7500
item 2: 0.7606
item 3: 0.7714
item 4: 0.7826
```
