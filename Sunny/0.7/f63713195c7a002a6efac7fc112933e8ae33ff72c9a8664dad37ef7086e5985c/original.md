```
print_wrapped_intensities(sys::System; nmax=10)
```

For Bravais lattices: Prints up to `nmax` wavevectors according to their instantaneous (static) structure factor intensities, listed in descending order. For non-Bravais lattices: Performs the same analysis for each spin sublattice independently; the output weights are naïvely averaged over sublattices, without incorporating phase shift information. This procedure therefore wraps all wavevectors into the first Brillouin zone. Each wavevector coordinate is given between $-1/2$ and $1/2$ in reciprocal lattice units (RLU).  The output from this function will typically be used as input to [`suggest_magnetic_supercell`](@ref).

Because this function does not incorporate phase information in its averaging over sublattices, the printed weights are not directly comparable with experiment. For that purpose, use [`SampledCorrelationsStatic`](@ref) instead.
