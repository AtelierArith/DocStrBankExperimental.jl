```
monoiso_mass_unc(atomsymbol::Symbol) -> Tuple{Float64,Float64}
monoiso_mass_unc(atom) -> Tuple{Float64,Float64}
monoiso_mass_unc(mol::MolGraph) -> Tuple{Float64,Float64}
```

Return a tuple of monoisotopic mass of the atom/molecule and its uncertainty.

Monoisotopic mass is the relative atomic mass of the most abundant isotope. Even if there is specific `Atom.mass` value, it will be ignored.
