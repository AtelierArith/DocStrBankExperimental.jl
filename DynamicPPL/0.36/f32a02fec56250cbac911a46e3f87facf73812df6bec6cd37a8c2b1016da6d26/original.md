```
subset(varinfo::AbstractVarInfo, vns::AbstractVector{<:VarName})
```

Subset a `varinfo` to only contain the variables `vns`.

The ordering of variables in the return value will be the same as in `varinfo`.

# Examples

```jldoctest varinfo-subset; setup = :(using Distributions, DynamicPPL)
julia> @model function demo()
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, sqrt(s))
           x = Vector{Float64}(undef, 2)
           x[1] ~ Normal(m, sqrt(s))
           x[2] ~ Normal(m, sqrt(s))
       end
demo (generic function with 2 methods)

julia> model = demo();

julia> varinfo = VarInfo(model);

julia> keys(varinfo)
4-element Vector{VarName}:
 s
 m
 x[1]
 x[2]

julia> for (i, vn) in enumerate(keys(varinfo))
           varinfo[vn] = i
       end

julia> varinfo[[@varname(s), @varname(m), @varname(x[1]), @varname(x[2])]]
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> # Extract one with only `m`.
       varinfo_subset1 = subset(varinfo, [@varname(m),]);


julia> keys(varinfo_subset1)
1-element Vector{VarName{:m, typeof(identity)}}:
 m

julia> varinfo_subset1[@varname(m)]
2.0

julia> # Extract one with both `s` and `x[2]`.
       varinfo_subset2 = subset(varinfo, [@varname(s), @varname(x[2])]);

julia> keys(varinfo_subset2)
2-element Vector{VarName}:
 s
 x[2]

julia> varinfo_subset2[[@varname(s), @varname(x[2])]]
2-element Vector{Float64}:
 1.0
 4.0
```

`subset` is particularly useful when combined with [`merge(varinfo::AbstractVarInfo)`](@ref)

```jldoctest varinfo-subset
julia> # Merge the two.
       varinfo_subset_merged = merge(varinfo_subset1, varinfo_subset2);

julia> keys(varinfo_subset_merged)
3-element Vector{VarName}:
 m
 s
 x[2]

julia> varinfo_subset_merged[[@varname(s), @varname(m), @varname(x[2])]]
3-element Vector{Float64}:
 1.0
 2.0
 4.0

julia> # Merge the two with the original.
       varinfo_merged = merge(varinfo, varinfo_subset_merged);

julia> keys(varinfo_merged)
4-element Vector{VarName}:
 s
 m
 x[1]
 x[2]

julia> varinfo_merged[[@varname(s), @varname(m), @varname(x[1]), @varname(x[2])]]
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

# Notes

## Type-stability

!!! warning
    This function is only type-stable when `vns` contains only varnames with the same symbol. For exmaple, `[@varname(m[1]), @varname(m[2])]` will be type-stable, but `[@varname(m[1]), @varname(x)]` will not be.

