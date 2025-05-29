```
fill_in_supports!(pref::IndependentParameterRef;
                  [num_supports::Int = DefaultNumSupports])::Nothing
```

Automatically generate support points for a particular independent parameter `pref`. Generating `num_supports` for the parameter. The supports are generated uniformly if the underlying infinite domain is an `IntervalDomain` or they are generating randomly accordingly to the distribution if the domain is a `UniDistributionDomain`. Will add nothing if there are supports and `modify = false`. Extensions that use user defined domain types should extend [`generate_and_add_supports!`](@ref) and/or [`generate_support_values`](@ref) as needed. Errors if the infinite domain type is not recognized.

**Example**

```julia-repl
julia> fill_in_supports!(x, num_supports = 4)

julia> supports(x)
4-element Array{Number,1}:
 0.0
 0.333
 0.667
 1.0

```
