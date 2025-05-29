```
intensities_static(swt::SpinWaveTheory, qpts; bounds=(-Inf, Inf), kernel=nothing, kT=0)
intensities_static(sc::SampledCorrelations, qpts; bounds=(-Inf, Inf), kT)
intensities_static(sc::SampledCorrelationsStatic, qpts)
```

Like [`intensities`](@ref), but integrates the dynamical correlations $\mathcal{S}(𝐪, ω)$ over a range of energies $ω$. By default, the integration `bounds` are $(-∞, ∞)$, yielding the instantaneous (equal-time) correlations.

In [`SpinWaveTheory`](@ref), the integral will be realized as a sum over discrete bands. Alternative calculation methods are [`SpinWaveTheorySpiral`](@ref) and [`SpinWaveTheoryKPM`](@ref).

Classical dynamics data in [`SampledCorrelations`](@ref) can also be used to calculate static intensities. In this case, the domain of integration will be a finite grid of available `energies`. Here, the parameter `kT` will be used to account for the quantum thermal occupation of excitations, as documented in [`intensities`](@ref).

Static intensities calculated from [`SampledCorrelationsStatic`](@ref) are dynamics-independent. Instead, instantaneous correlations sampled from the classical Boltzmann distribution will be reported.
