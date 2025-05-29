```
monoiso_mass_unc(atomsymbol::Symbol) -> Tuple{Float64,Float64}
monoiso_mass_unc(atom) -> Tuple{Float64,Float64}
monoiso_mass_unc(mol::MolGraph) -> Tuple{Float64,Float64}
```

原子または分子の単一同位体質量とその不確かさのタプルを返します。

単一同位体質量は、最も豊富な同位体の相対原子質量です。特定の `Atom.mass` 値があっても、それは無視されます。
