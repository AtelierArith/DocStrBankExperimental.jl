```
symmetry_equivalent_bonds(sys::System, bond::Bond)
```

Given a [`Bond`](@ref) for the original (unreshaped) crystal, return all symmetry equivalent bonds in the [`System`](@ref). Each returned bond is represented as a pair of [`Site`](@ref)s and an `offset`, which may be used as input to [`set_exchange_at!`](@ref) or [`set_pair_coupling_at!`](@ref). Reverse bonds are not included in the iterator (no double counting).

# Example

```julia
for (site1, site2, offset) in symmetry_equivalent_bonds(sys, bond)
    @assert site1 < site2
    set_exchange_at!(sys, J, site1, site2; offset)
end
```
