```
SpinWaveTheorySpiral(sys::System; k, axis, measure, regularization=1e-8)
```

Analogous to [`SpinWaveTheory`](@ref), but interprets the provided system as having a generalized spiral order. This order is described by a single propagation wavevector `k`, which may be incommensurate. The `axis` vector defines the polarization plane via its surface normal. Typically the spin configuration in `sys` and the propagation wavevector `k` will be optimized using [`minimize_spiral_energy!`](@ref). In contrast, `axis` will typically be determined from symmetry considerations.

The resulting object can be used to calculate the spin wave [`dispersion`](@ref), or the structure factor via [`intensities_bands`](@ref) and [`intensities`](@ref).

The algorithm for this calculation was developed in [Toth and Lake, J. Phys.: Condens. Matter **27**, 166002 (2015)](https://arxiv.org/abs/1402.6069) and implemented in the [SpinW code](https://spinw.org/).
