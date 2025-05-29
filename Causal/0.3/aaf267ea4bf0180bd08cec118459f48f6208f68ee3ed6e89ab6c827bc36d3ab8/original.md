```julia
struct Outport{P} <: Causal.AbstractPort{P}
```

Constructs an `Outport` with `numpins` [`Outpin`](@ref).

# Fields

  * `pins::Vector`: Pins of the output port
  * `id::Base.UUID`: Unique identifier

!!! warning Element type of an `Outport` must be `Outpin`. See also [`Outpin`](@ref)

# Example

```jldoctest
julia> Outport{Int}(2)
2-element Outport{Outpin{Int64}}:
 Outpin(eltype:Int64, isbound:false)
 Outpin(eltype:Int64, isbound:false)

julia> Outport()
1-element Outport{Outpin{Float64}}:
 Outpin(eltype:Float64, isbound:false)
```
