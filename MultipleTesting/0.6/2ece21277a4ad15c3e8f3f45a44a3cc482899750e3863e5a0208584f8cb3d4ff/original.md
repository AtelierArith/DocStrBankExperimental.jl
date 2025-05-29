```
combine(PValues, <:PValueCombination)
```

Combine p-values

# Examples

```jldoctest
julia> pvals = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pvals, Fisher())
0.007616871850449092

julia> combine(pvals, Stouffer())
0.00709832618126593
```

# See also

`PValueCombination`s:

[`Fisher`](@ref) [`Logit`](@ref) [`Stouffer`](@ref) [`Tippett`](@ref) [`Simes`](@ref) [`Wilkinson`](@ref) [`Minimum`](@ref)
