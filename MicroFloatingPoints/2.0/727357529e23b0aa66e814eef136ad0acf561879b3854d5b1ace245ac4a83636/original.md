```
FloatmuIterator(start::Floatmu{szE,szf},stop::Floatmu{szE,szf},
                step::Floatmu{szE,szf}) where {szE,szf}
FloatmuIterator(start::Floatmu{szE,szf},stop::Floatmu{szE,szf},
                step::Float64) where {szE,szf}
FloatmuIterator(start::Floatmu{szE,szf},stop::Floatmu{szE,szf},
                step::Int = 1) where {szE,szf}
FloatmuIterator(::Type{Floatmu{szE,szf}},start::Float64,stop::Float64,
                step::Int = 1) where {szE,szf}
FloatmuIterator(::Type{Floatmu{szE,szf}},start::Float64,stop::Float64,
                step::Float64) where {szE,szf}
```

Iterator to generate all `Floatmu{szE,szf}` in the domain `[start,stop]`. The iterator can be initialized with two `Floatmu{szE,szf}` or with two `Float64`. 

One may iterate from one float to the next (the default) or choose some step.  The step may be a number of floats or an amount to add.

An ArgumentError is raised if the bounds are NaNs, if the step chosen is zero (or rounds to zero when converted to a `Floatmu{szE,szf}`), or if the step is a value smaller than the largest distance between two consecutive floats in `[last, stop]` (use [`eligible_step`](@ref) to know the smallest value allowed).

When the step is an amount to add, the bounds cannot be infinities. 

When the step is a number of floats, infinities are allowed for the bounds and are always part of the resulting range:

```jldoctest
julia> collect(FloatmuIterator(Floatmu{2,2},-Inf,Inf,5))
6-element Vector{Floatmu{2, 2}}:
 -Infμ{2, 2}
  -1.8
  -0.5
   0.75
   2.0
  Infμ{2, 2}
```

# Examples

```jldoctest
julia> L=[x for x = FloatmuIterator(Floatmu{2, 2}(0.0), Floatmu{2, 2}(1.0))]
5-element Vector{Floatmu{2, 2}}:
 0.0
 0.25
 0.5
 0.75
 1.0
julia> L2=[x for x = FloatmuIterator(Floatmu{2, 2}, 0.0, 1.0, 2)]
3-element Vector{Floatmu{2, 2}}:
 0.0
 0.5
 1.0
```
