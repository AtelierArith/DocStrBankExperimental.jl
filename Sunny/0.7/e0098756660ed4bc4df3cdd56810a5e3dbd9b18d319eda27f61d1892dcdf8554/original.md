```
suggest_magnetic_supercell(ks; tol=1e-12, maxsize=100)
```

Suggests a magnetic supercell, in units of the crystal lattice vectors, that is consistent with periodicity of the wavevectors `ks` in RLU. If the wavevectors are incommensurate (with respect to the maximum supercell size `maxsize`), one can select a larger error tolerance `tol` to find a supercell that is almost commensurate.

Prints a $3×3$ matrix of integers that is suitable for use in [`reshape_supercell`](@ref).

# Examples

```julia
# A magnetic supercell for a single-Q structure. Will print
k1 = [0, -1/4, 1/4]
suggest_magnetic_supercell([k1])       # [1 0 0; 0 2 1; 0 -2 1]

# A larger magnetic supercell for a double-Q structure
k2 = [1/4, 0, 1/4]
suggest_magnetic_supercell([k1, k2])   # [1 2 2; -1 2 -2; -1 2 2]

# If given incommensurate wavevectors, find an approximate supercell that
# is exactly commensurate for nearby wavevectors.
suggest_magnetic_supercell([[0, 0, 1/√5], [0, 0, 1/√7]]; tol=1e-2)

# This prints [1 0 0; 0 1 0; 0 0 16], which becomes commensurate under the
# approximations `1/√5 ≈ 7/16` and `1/√7 ≈ 3/8`.
```
