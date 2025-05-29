```
@rulenode
```

Construct a [`RuleNode`](@ref) using the shorthand notation [`RuleNode`](@ref)s and [`AbstractHole`](@ref)s are printed with using [`Base.show`](@ref).

Does not yet support [`AbstractHole`](@ref)s defined outside of [`HerbCore`](@ref).

!!! note "Hole domain representation"
    [`AbstractHole`](@ref)s' domains are printed with a `Bool[...]` surrounding them. The macro accepts the domain with or without the `Bool[...]`: `UniformHole[Bool[1, 1, 0, 0]]{2,3}` and `UniformHole[1, 1, 0, 0]{2,3}` both work.


# Examples

```jldoctest
julia> @rulenode 1{4{5,6},1{2,3}}
1{4{5,6},1{2,3}}

julia> @rulenode 1
1

julia> @rulenode 1{2, 3}
1{2,3}

julia> @rulenode UniformHole[1, 1, 0, 0]{2,3}
UniformHole[Bool[1, 1, 0, 0]]{2,3}

julia> @rulenode Hole[1, 1, 0, 0]
Hole[Bool[1, 1, 0, 0]]

```
