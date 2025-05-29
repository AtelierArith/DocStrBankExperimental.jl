```julia
struct Jeckelmann <: MPSKit.DDMRG_Flavour
```

The original flavour of dynamical DMRG, which minimizes the following (quadratic) cost function:

$$
|| (H - E) |ψ₀⟩ - |ψ⟩ ||
$$

See also [`NaiveInvert`](@ref) for a less costly but less accurate alternative.

## References

  * [Jeckelmann. Phys. Rev. B 66 (2002)](@cite jeckelmann2002)
