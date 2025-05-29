```julia
struct Inport{P} <: Causal.AbstractPort{P}
```

Constructs an `Inport` with `numpins` [`Inpin`](@ref).

# Fields

  * `pins::Vector`: Pins of the port

!!! warning Element type of an `Inport` must be `Inpin`. See also [`Inpin`](@ref)

# Example

```jldoctest
julia> Inport{Int}(2)
2-element Inport{Inpin{Int64}}:
 Inpin(eltype:Int64, isbound:false)
 Inpin(eltype:Int64, isbound:false)

julia> Inport()
1-element Inport{Inpin{Float64}}:
 Inpin(eltype:Float64, isbound:false)
```
