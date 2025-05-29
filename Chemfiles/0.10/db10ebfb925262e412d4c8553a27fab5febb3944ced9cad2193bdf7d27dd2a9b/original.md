```julia
add_atom!(
    frame::Chemfiles.Frame,
    atom::Chemfiles.Atom,
    position::Vector{Float64}
)
add_atom!(
    frame::Chemfiles.Frame,
    atom::Chemfiles.Atom,
    position::Vector{Float64},
    velocity::Vector{Float64}
)

```

Add an `atom` and the corresponding `position` and `velocity` data to a `frame`.
