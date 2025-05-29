```
modify_exchange_with_truncated_dipole_dipole!(sys::System, cutoff, μ0_μB²)
```

Like [`enable_dipole_dipole!`](@ref), the purpose of this function is to introduce long-range dipole-dipole interactions between magnetic moments. Whereas `enable_dipole_dipole!` employs Ewald summation, this function instead employs real-space pair couplings with truncation at the specified `cutoff` distance. If the cutoff is relatively small, then this function may be faster than `enable_dipole_dipole!`.

!!! warning "Mutation of existing couplings"
    This function will modify existing bilinear couplings between spins by adding dipole-dipole interactions. It must therefore be called *after* all other pair couplings have been specified. Conversely, any calls to `set_exchange!`, `set_pair_coupling!`, etc. will irreversibly delete the dipole-dipole interactions that have been introduced by this function.

