```julia
struct Species
```

Represents a gas with a specific charge state. In a plasma, different ionization states of the same gas may coexist, so we need to be able to differentiate between these.

# Fields

  * `element::HallThruster.Gas`: The gas that forms the base of the species
  * `Z::Int64`: The charge state of the species, i.e. Z = 1 for a singly-charged species
  * `symbol::Symbol`: The symbol of the species, i.e. `Symbol(Xe+)` for `Species(Xenon, 1)`

```jldoctest;setup = :(using HallThruster: Xenon, Species)
julia> Species(Xenon, 0)
Xe

julia> Species(Xenon, 1)
Xe+

julia> Species(Xenon, 3)
Xe3+
```
