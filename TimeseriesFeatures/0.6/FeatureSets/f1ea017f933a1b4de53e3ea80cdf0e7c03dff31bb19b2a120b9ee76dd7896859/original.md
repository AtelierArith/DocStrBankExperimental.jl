```
FeatureSet(methods, [names, keywords, descriptions])
FeatureSet(features::Vector{T}) where {T <: AbstractFeature}
```

Construct a `FeatureSet` from `methods` (a vector of functions) and optionally provide `names` as a vector of symbols, `descriptions` as a vector of strings, and `keywords` as a vector of vectors of strings. A `FeatureSet` can be called on a time-series vector or matrix `X` (with time series occupying columns) to return a `FeatureArray` of feature values. Subsets of a `FeatureSet` `𝒇` can be obtained by indexing with feature names (as symbols) or the regular linear and logical indices. `FeatureSet`s also support simple set operations defined for arrays, such as unions and intersections, as well as convenient syntax for concatenation (`+`) and set differencing (`\`). Note that two features are considered the same (`isequal') if and only if their names are equal.

# Examples

```julia
𝒇 = FeatureSet([sum, length], [:sum, :length], ["∑x¹", "∑x⁰"], [["distribution"], ["sampling"]])
X = randn(100, 2) # 2 time series, 100 samples long
F = 𝒇(X)

# Joining feature sets
𝒇₁ = FeatureSet([x->min(x...), x->max(x...)], [:min, :max], ["minimum", "maximum"], [["distribution"], ["distribution"]])
𝒈₁ = 𝒇 + 𝒇₁
G = 𝒈₁(X)

# Intersecting feature sets, where features are identified exclusively by their names
𝒇₂ = FeatureSet(x->prod, :sum, "∏x", ["distributions"])
𝒈₂ = 𝒇 ∩ 𝒇₂ # The intersection of two feature sets, both with their own :sum
G = 𝒈₂(X) # The intersection contains the :sum of the first argument to ∩; 𝒇
```
