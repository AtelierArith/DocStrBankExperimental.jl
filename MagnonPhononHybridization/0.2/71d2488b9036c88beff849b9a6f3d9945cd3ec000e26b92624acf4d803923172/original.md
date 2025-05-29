```
LSWT(
    lattice::Lattice,
    hilbert::Hilbert{<:CompositeInternal{<:SpinPhonon}},
    terms::OneOrMore{Term},
    magneticstructure::MagneticStructure;
    neighbors::Union{Int, Neighbors}=nneighbor(terms)
)
```

Construct a LSWT for a magnon-phonon coupled system.
