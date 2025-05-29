```
product_distribution(dists::AbstractArray{<:Distribution{<:ArrayLikeVariate{M}},N})
```

Create a distribution of `M + N`-dimensional arrays as a product distribution of independent `M`-dimensional distributions by stacking them.

The function falls back to constructing a [`ProductDistribution`](@ref) distribution but specialized methods can be defined.
