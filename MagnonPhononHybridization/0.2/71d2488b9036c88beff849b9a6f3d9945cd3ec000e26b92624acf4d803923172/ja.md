```
LSWT(
    lattice::Lattice,
    hilbert::Hilbert{<:CompositeInternal{<:SpinPhonon}},
    terms::OneOrMore{Term},
    magneticstructure::MagneticStructure;
    neighbors::Union{Int, Neighbors}=nneighbor(terms)
)
```

マグノン-フォノン結合系のためのLSWTを構築します。
