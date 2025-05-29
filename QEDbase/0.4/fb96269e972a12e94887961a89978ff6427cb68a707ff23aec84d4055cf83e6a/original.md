Concrete type indicating that a particle with [`is_fermion`](@ref) has an indefinite spin and the differential cross section calculation should average or sum over all spins, depending on the direction ([`Incoming`](@ref) or [`Outgoing`](@ref)) of the particle in question.

```jldoctest
julia> using QEDbase

julia> AllSpin()
all spins
```
