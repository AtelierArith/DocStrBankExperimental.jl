```julia
bond_order(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer
) -> Chemfiles.BondOrder

```

Get the `BondOrder` for the bond between atoms `i` and `j` in the `topology`.
