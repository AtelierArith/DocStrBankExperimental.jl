```
pwc_density(x::AbstractVector)
```

量子粒子の位置から得られる区分定数確率密度を返します。

量子粒子が位置 `x₀, x₁, …, xₙ` にあるとします（Julia では実際には `x[1], x[2], ..., x[n], x[n+1]` であることに注意してください）。返される配列 `R` は `R[1] = R[n+2] = 0` であり、間のインデックスに対して `R[i] = 1 / (n * (x[i] - x[i-1]))` となります（この式は、`x[0] = -∞` および `x[n+2] = ∞` と仮定すれば、最初と最後のエントリにも当てはまります）。

# 例

```jldoctest
julia> pwc_density([0, 1, 3])
4-element Vector{Float64}:
 0.0
 0.5
 0.25
 0.0
```
