```
standard_weight_unc(atomsymbol::Symbol) -> Tuple{Float64,Float64}
standard_weight_unc(atom) -> Tuple{Float64,Float64}
standard_weight_unc(mol::MolGraph) -> Tuple{Float64,Float64}
```

Return a tuple of standard atomic weight (or molecular weight) and its uncertainty.

If `Atom.mass` is specified, calculated exact mass of the atom will be used instead. 
