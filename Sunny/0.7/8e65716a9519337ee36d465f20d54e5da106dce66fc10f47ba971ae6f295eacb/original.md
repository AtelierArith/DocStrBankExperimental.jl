```
set_pair_coupling!(sys::System, op, bond)
```

Sets an arbitrary coupling `op` along `bond`. This coupling will be propagated to equivalent bonds in consistency with crystal symmetry. Any previous interactions on these bonds will be overwritten. The parameter `bond` has the form `Bond(i, j, offset)`, where `i` and `j` are atom indices within the unit cell, and `offset` is a displacement in unit cells. The operator `op` may be provided as an anonymous function that accepts two spin dipole operators, or as a matrix that acts in the tensor product space of the two sites.

# Examples

```julia
# Bilinear+biquadratic exchange involving 3×3 matrices J1 and J2
set_pair_coupling!(sys, (Si, Sj) -> Si'*J1*Sj + (Si'*J2*Sj)^2, bond)

# Equivalent expression using an appropriate fixed matrix representation
S = spin_matrices(1/2)
Si, Sj = to_product_space(S, S)
set_pair_coupling!(sys, Si'*J1*Sj + (Si'*J2*Sj)^2, bond)
```

See also [`spin_matrices`](@ref), [`to_product_space`](@ref).
