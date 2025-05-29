```julia
is_geminal(
    a1::BiochemicalAlgorithms.Atom,
    a2::BiochemicalAlgorithms.Atom
) -> Union{Missing, Bool}

```

Decides if two atoms are geminal.

Two atoms are geminal if they do not share a common bond but both have a bond to a third atom. For example the two hydrogen atoms in water are geminal. Hydrogen bonds (`has_flag(bond, :TYPE__HYDROGEN)`) are ignored.
