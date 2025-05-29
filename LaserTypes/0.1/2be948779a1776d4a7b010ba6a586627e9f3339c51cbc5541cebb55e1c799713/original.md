```
struct LaguerreGaussLaser <: AbstractLaser
```

The `LaguerreGaussLaser` is defined by the `units` of the laser (a positional argument that can be `:SI`, `:atomic` or `:SI_unitful` and `:atomic_unitful`) and the following parameters

  * `λ` is the laser wavelangth
  * `a₀` is the normalized vector potential (defined as $a_0=\frac{eA}{m_e c^2}$)
  * `ϕ₀` is the initial phase with the default value 0.0
  * `w₀` is the beam radius at the Rayleigh range or [beam waist](https://en.wikipedia.org/wiki/Gaussian_beam#Beam_waist)
  * `ξx` and `ξy` give the polarization and have the default value `1.0 + 0im` and `0.0 + 0im`
  * `orientation` specifies how the laser is oriented with respect to the

default coordinate system (default `(:x, :z)`). See [`LaserGeometry`](@ref) for more details.

  * `propagation_dir` is the propagation direction of the wave in the

intrinsic coordinate system (default `:z`). See [`LaserGeometry`](@ref) for more details.

  * `profile` is the temporal profile of the pulse and the default one is constant (infinite pules duration)
  * `p` is the radial index of the mode, $p ∈ ℤ, p ≥ 0$, with the default value 1
  * `m` is the azimuthal index of the mode, $m ∈ ℤ$, with the default value 0

During the initialization of the `LaguerreGaussLaser` type, some useful derived values are also computed

  * `ω` is the angular frequency and is given by $2π c / λ$
  * `k` is the wavenumber and is given by $2π / λ$
  * `z_R` is the [Rayleigh range](https://en.wikipedia.org/wiki/Rayleigh_length) and is given by $k w_0^2 / 2$
  * `T₀` is the laser period and is given by $2π / ω$
  * `E₀` is the amplitude of the electric field and is given by $a_0\frac{m_q c \omega}{q}$
  * `Nₚₘ` is a normalization factor given by $\sqrt{(p+1)_{|m|}}$, with $(x)_n$ the [Pochhammer symbol](https://mathworld.wolfram.com/PochhammerSymbol.html)
