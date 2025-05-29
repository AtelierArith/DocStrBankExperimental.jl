```
set_onsite_coupling!(sys::System, op, i::Int)
```

Set the single-ion anisotropy for the `i`th atom of every unit cell, as well as all symmetry-equivalent atoms. The operator `op` may be provided as an abstract function of the local spin operators, as a polynomial of [`spin_matrices`](@ref), or as a linear combination of [`stevens_matrices`](@ref).

# Examples

```julia
# An easy axis anisotropy in the z-direction
set_onsite_coupling!(sys, S -> -D*S[3]^3, i)

# The unique quartic single-ion anisotropy for a site with cubic point group
# symmetry
set_onsite_coupling!(sys, S -> 20*(S[1]^4 + S[2]^4 + S[3]^4), i)

# An equivalent expression of this quartic anisotropy, up to a constant shift
O = stevens_matrices(spin_label(sys, i))
set_onsite_coupling!(sys, O[4,0] + 5*O[4,4], i)
```

!!! warning "Limitations arising from quantum spin operators"
    Single-ion anisotropy is physically impossible for local moments with quantum spin $s = 1/2$. Consider, for example, that any Pauli matrix squared gives the identity. More generally, one can verify that the $k$th order Stevens operators `O[k, q]` are zero whenever $s < k/2$. Consequently, an anisotropy quartic in the spin operators requires $s ≥ 2$ and an anisotropy of sixth order requires $s ≥ 3$. To circumvent this physical limitation, Sunny provides a mode `:dipole_uncorrected` that naïvely replaces quantum spin operators with classical moments. See the documentation page [Interaction Renormalization](@ref) for more information.

