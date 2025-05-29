```
Atom(identifier::AtomId, position::AbstractVector; kwargs...)
Atom(identifier::AtomId, position::AbstractVector, velocity::AbstractVector; kwargs...)
Atom(; atomic_number, position, velocity=zeros(D)u"bohr/s", kwargs...)
```

Construct an atomic located at the cartesian coordinates `position` with (optionally) the given cartesian `velocity`. Note that `AtomId = Union{Symbol,AbstractString,Integer,ChemicalSymbol}`.

Supported `kwargs` include `species`, `mass`, as well as user-specific custom properties.
