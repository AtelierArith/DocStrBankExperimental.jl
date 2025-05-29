```julia
domain_label(transformation, index)

```

Return a string that can be used to for identifying a coordinate. Mainly for debugging and generating graphs and data summaries.

Transformations may provide a heuristic label.

Transformations should implement `_domain_label`.

# Example

```jldoctest
julia> t = as((a = asℝ₊,
            b = as(Array, asℝ₋, 1, 1),
            c = corr_cholesky_factor(2)));

julia> [domain_label(t, i) for i in 1:dimension(t)]
3-element Vector{String}:
 ".a"
 ".b[1,1]"
 ".c[1]"
```
