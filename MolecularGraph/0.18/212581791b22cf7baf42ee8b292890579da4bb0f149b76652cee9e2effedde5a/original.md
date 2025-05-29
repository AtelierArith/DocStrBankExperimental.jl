```
isotopiccomposition(atomsymbol::Symbol, number::Int; threshold=0.001
    ) -> Vector{Tuple{Float64,Float64}}
isotopiccomposition(mol::MolGraph; threshold=0.001
    ) -> Vector{Tuple{Float64,Float64}}
```

Return isotopic composition of the atoms/molecule as a vector of tuples of mass and composition.

Records that have lower abundance than the given threshold will be filtered out (default 0.001 = 0.1%)
