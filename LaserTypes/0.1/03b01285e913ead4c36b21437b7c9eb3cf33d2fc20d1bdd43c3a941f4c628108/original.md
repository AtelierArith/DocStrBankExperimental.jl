```
setup_laser(laser, units; τ=nothing, kwargs...)
```

Initialize the specified `laser` using the default parameteres in the specified `units`. Supported units are

  * `:SI`: Values are in SI, the numeric types are regular numbers (`Float64`)
  * `:SI_unitful`: Values are in SI, but using [Unitful.jl](https://github.com/PainterQubits/Unitful.jl)
  * `:atomic`: Values are in atomic units, the numeric types are regular numbers (`Float64`)
  * `:atomic_unitful`: Values are in atomic units, but using [UnitfulAtomic.jl](https://github.com/sostock/UnitfulAtomic.jl)

The keyword arguments can be used to give specific values to the parameters instead of using the defaults. You can specify parameteres such as the wavelength `λ` (default `0.8u"μm"`), beam waist `w₀` (default `58.0u"μm"`) and the normalized vector potential `a₀` (default `1`).

You can also use equivalent descriptions, such as passing the angular frequency `ω` or the wave number `k` instead of `λ` and the [Rayleigh range](https://en.wikipedia.org/wiki/Rayleigh_length) `z_R` instead of `z₀`. The duration of the pulse (assuming Gaussian temporal profile) can be given via `τ` (default `18.0u"fs"`).

You can also specify dimensionless parameteres such the initial phase (`ϕ₀`) and the polarization (`ξx` and `ξy`). The laser amplitude can be also specified through `E₀`.

By default the laser propagates along the `Oz` direction and osillates along the `Ox` direction. If you want to change that, you can use the `propagation_dir` and `orientation` arguments. See [Laser Geometry](@ref) for more details. See also the docomuntation for each laser type for more details on the additional supported arguments.
