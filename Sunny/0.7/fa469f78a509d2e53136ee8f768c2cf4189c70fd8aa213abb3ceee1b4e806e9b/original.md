```
SampledCorrelations(sys::System; measure, energies, dt)
```

An object to accumulate samples of dynamical pair correlations. The `measure` argument specifies a pair correlation type, e.g. [`ssf_perp`](@ref). The `energies` must be evenly-spaced and starting from 0, e.g. `energies = range(0, 3, 100)`. Select the integration time-step `dt` according to accuracy and speed considerations. [`suggest_timestep`](@ref) can help in selecting an appropriate value.

Dynamical correlations will be accumulated through calls to [`add_sample!`](@ref), which expects a spin configuration in thermal equilibrium. A classical spin dynamics trajectory will be simulated of sufficient length to achieve the target energy resolution. The resulting data can can then be extracted as pair-correlation [`intensities`](@ref) with appropriate classical-to-quantum correction factors. See also [`intensities_static`](@ref), which integrates over energy.
