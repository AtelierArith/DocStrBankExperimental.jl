```julia
pseudofile(
    family::PseudoPotentialData.PseudoFamily,
    element::Symbol
) -> String

```

Get the full path to the file containing the pseudopotential information for a particular `element` (identified by an atomic symbol) and a particular pseudopotential `family`.
