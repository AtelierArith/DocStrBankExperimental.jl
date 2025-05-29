```julia
is_bound_to(
    a1::BiochemicalAlgorithms.Atom,
    a2::BiochemicalAlgorithms.Atom
) -> Bool

```

Decides if two atoms are bound to each other. Hydrogen bonds (`has_flag(bond, :TYPE__HYDROGEN)`) are ignored.
