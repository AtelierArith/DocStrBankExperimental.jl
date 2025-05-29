```
struct SmoothErsatzMaterialInterpolation{M<:Vector{<:Number},N<:Vector{<:Number}}
```

A wrapper holding parameters and methods for interpolating an integrand across a single boundary $\partial\Omega$.

E.g., $\int f~\mathrm{d}\Omega = \int I(\varphi)f~\mathrm{d}D$ where $\Omega\subset D$ is described by a level-set function $\varphi$ and $I$ is an indicator function.

# Properties

  * `η::M`: the interpolation or smoothing radius across ∂Ω
  * `ϵ::M`: the ersatz material density
  * `H`: a smoothed Heaviside function
  * `DH`: the derivative of `H`
  * `I`: an indicator function
  * `ρ`: a function describing the volume density of $\Omega$ (e.g., $\mathrm{Vol}(\Omega) = \int \rho(\varphi))~\mathrm{d}D)$

# Note

  * We store η and ϵ as length-one vectors so that updating these values propagates through H, DH, etc.
  * To update η and/or ϵ in an instance `m`, take `m.η .= <VALUE>`.
  * A conviencence constructor is provided to create an instance given `η<:Number` and `ϵ<:Number`.
