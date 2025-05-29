```
Spectrum(c::CorrelationFunction, ps=[]; kwargs...)
```

Create an instance of [`Spectrum`](@ref) corresponding to the Fourier transform of the [`CorrelationFunction`](@ref) `c`.

# Examples

```
julia> c = CorrelationFunction(a',a,de;steady_state=true)
⟨a′*a_0⟩

julia> S = Spectrum(c)
ℱ(⟨a′*a_0⟩)(ω)
```
