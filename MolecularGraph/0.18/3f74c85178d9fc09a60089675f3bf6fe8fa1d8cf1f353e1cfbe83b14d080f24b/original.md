```
exact_mass_unc(atomsymbol::Symbol, [number::Union{Int, Nothing}]) -> Tuple{Float64,Float64}
exact_mass_unc(atom) -> Tuple{Float64,Float64}
exact_mass_unc(mol::MolGraph) -> Tuple{Float64,Float64}
```

Return a tuple of calculated exact mass and its uncertainty.

If `number` is not given or `Atom.mass` is not specified, monoisotopic mass will be used instead.
