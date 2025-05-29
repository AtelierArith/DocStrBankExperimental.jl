```
add_supports(pref::IndependentParameterRef,
             supports::Union{Real, Vector{<:Real}};
             [label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

`pref` に識別ラベル `label` を持つ追加のサポートポイントを追加します。

**例**

```julia-repl
julia> add_supports(t, 0.5)

julia> supports(t)
3-element Array{Float64,1}:
 0.0
 0.5
 1.0

julia> add_supports(t, [0.25, 1])

julia> supports(t)
4-element Array{Float64,1}:
 0.0
 0.25
 0.5
 1.0
```
