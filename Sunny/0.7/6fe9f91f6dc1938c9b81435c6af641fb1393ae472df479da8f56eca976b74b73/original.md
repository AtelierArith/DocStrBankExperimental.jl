```
SampledCorrelationsStatic(sys::System; measure)
```

An object to accumulate samples of static pair correlations. It is similar to [`SampledCorrelations`](@ref), but no time-integration will be performed on calls to [`add_sample!`](@ref). The resulting object can be used with [`intensities_static`](@ref) to calculate statistics from the classical Boltzmann distribution. Dynamical [`intensities`](@ref) data, however, will be unavailable. Similarly, classical-to-quantum corrections that rely on the excitation spectrum cannot be performed.
