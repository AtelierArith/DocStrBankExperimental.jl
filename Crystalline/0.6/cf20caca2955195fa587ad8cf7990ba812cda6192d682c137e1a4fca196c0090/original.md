```
cartesianize(op::SymOperation{D}, Rs::DirectBasis{D}) --> SymOperation{D}
```

Converts `opˡ` from a lattice basis to a Cartesian basis, by computing the transformed operators `opᶜ = 𝐑*opˡ*𝐑⁻¹` via the Cartesian basis matrix 𝐑 (whose columns are the `DirectBasis` vectors `Rs[i]`). 

# Note 1

The matrix 𝐑 maps vectors coefficients in a lattice basis 𝐯ˡ to coefficients in a Cartesian basis 𝐯ᶜ as 𝐯ˡ = 𝐑⁻¹𝐯ᶜ and vice versa as 𝐯ᶜ = 𝐑𝐯ˡ. Since a general transformation P  transforms an "original" vectors with coefficients 𝐯 to new coefficients 𝐯′ via 𝐯′ = P⁻¹𝐯 and since we here here consider the lattice basis as the "original" basis we have P = 𝐑⁻¹.  As such, the transformation of the operator `op` transforms as `opᶜ = P⁻¹*opˡ*P`, i.e. `opᶜ = transform(opˡ,P) = transform(opˡ,𝐑⁻¹)`.

# Note 2

The display (e.g. Seitz and xyzt notation) of `SymOperation`s e.g. in the REPL implicitly assumes integer coefficients for its point-group matrix: as a consequence, displaying  `SymOperation`s in a Cartesian basis may produce undefined behavior. The matrix representation remains valid, however.
