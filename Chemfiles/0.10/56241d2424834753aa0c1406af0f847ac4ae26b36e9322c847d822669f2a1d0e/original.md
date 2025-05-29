```julia
add_bond!(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer
)
add_bond!(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer,
    order
)

```

Add a bond between the atoms `i` and `j` in the `topology`, optionaly setting the bond `order`.
