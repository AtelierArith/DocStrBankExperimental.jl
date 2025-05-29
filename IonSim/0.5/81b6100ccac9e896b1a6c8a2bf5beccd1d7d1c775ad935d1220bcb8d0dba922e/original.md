```
function full_normal_mode_description(
    M::Vector{<:Real}, Q::Vector{<:Int}, comfreqs::NamedTuple{(:x, :y, :z)}
)
```

Same thing but explicitly provide the masses `M` and charges `Q` of the ions.
