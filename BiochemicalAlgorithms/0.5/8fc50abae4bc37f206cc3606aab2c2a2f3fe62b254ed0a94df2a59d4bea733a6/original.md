```julia
is_vicinal(
    a1::BiochemicalAlgorithms.Atom,
    a2::BiochemicalAlgorithms.Atom
) -> Bool

```

Decides if two atoms are vicinal.

Two atoms are vicinal if they are separated by three bonds (1-4 position). Hydrogen bonds (`has_flag(bond, :TYPE__HYDROGEN)`) are ignored.
