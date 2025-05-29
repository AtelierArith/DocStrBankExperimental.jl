```
FixedAtomsProbabilityDistribution{threaded}
```

有限サポートと固定された原子を持つ確率分布。

期待値が微分されるとき、重みのみがアクティブと見なされ、原子は定数と見なされます。

# 例

```jldoctest
julia> using DifferentiableExpectations, Statistics, Zygote

julia> using DifferentiableExpectations: atoms, weights

julia> dist = FixedAtomsProbabilityDistribution([2, 3], [0.4, 0.6]);

julia> atoms(map(abs2, dist))
2-element Vector{Int64}:
 4
 9

julia> weights(map(abs2, dist))
2-element Vector{Float64}:
 0.4
 0.6

julia> mean(abs2, dist)
7.0

julia> gradient(mean, abs2, dist)[2]
(atoms = nothing, weights = [4.0, 9.0])
```

# コンストラクタ

```
FixedAtomsProbabilityDistribution(
    atoms::AbstractVector,
    weights::AbstractVector=uniform_weights(atoms);
    threaded=false
)
```

# フィールド

  * `atoms::AbstractVector`
  * `weights::AbstractVector{<:Real}`
