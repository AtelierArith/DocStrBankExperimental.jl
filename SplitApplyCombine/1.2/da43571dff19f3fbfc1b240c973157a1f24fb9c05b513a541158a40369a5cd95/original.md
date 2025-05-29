```
groupunique([by], [f], iter)
```

Return a dictionary mapping the sets of elements `x` of iter grouped by `by(x)` with values `f(x)`, where `by` and `f` default to the identity function.

This is similar to `unique.(group(by, f, iter))` but each subgroup is an `AbstractIndices` of distinct values (rather than an `AbstractArray` with possibly repeated values).

# Example

```julia
julia> groupunique(iseven, [1,2,1,2,3])
2-element Dictionary{Bool,Indices{Int64}}
 false │ {2}
  true │ {1, 3}
```
