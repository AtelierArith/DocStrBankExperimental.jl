```
SpinMC([M], M0, frac, T1, T2, Δf, τ, [pos]) <: AbstractSpin
```

Create an object that represents a single spin with multiple compartments.

# Properties

  * `M::MagnetizationMC = Meq`: Magnetization vector
  * `Meq::MagnetizationMC = MagnetizationMC((0, 0, frac[1] * M0), ...)`: Equilibrium magnetization vector
  * `M0::Real`: Equilibrium magnetization
  * `frac::Tuple{<:Real}`: Water fraction of each compartment
  * `T1::Tuple{<:Real}`: Spin-lattice recovery time constants (ms)
  * `T2::Tuple{<:Real}`: Spin-spin recovery time constants (ms)
  * `Δf::Tuple{<:Real}`: Off-resonance frequencies (Hz)
  * `r::Tuple{Tuple{<:Real}}`: Exchange rates (1/ms); `r[i][j]` is the exchange rate from compartment `i` to compartment `j`
  * `pos::Position = Position(0, 0, 0)`: Spatial location (cm)
  * `N::Int = length(frac)`: Number of compartments

## Note

The `SpinMC` constructor takes `τ` (inverse exchange rate, or residence time) as input, *not* `r`. Furthermore, `τ` is given as a `Tuple` with `N^2 - N` elements, arranged like (τ12, τ13, ..., τ1N, τ21, τ23, ..., τ2N, ...).

# Examples

```jldoctest
julia> SpinMC(1, (0.2, 0.8), (400, 1000), (20, 100), (15, 0), (100, 25))
SpinMC{Float64,2}:
 M = MagnetizationMC((0.0, 0.0, 0.2), (0.0, 0.0, 0.8))
 M0 = 1.0
 frac = (0.2, 0.8)
 T1 = (400.0, 1000.0) ms
 T2 = (20.0, 100.0) ms
 Δf = (15.0, 0.0) Hz
 r = ((0.0, 0.01), (0.04, 0.0)) 1/ms
 pos = Position(0.0, 0.0, 0.0) cm
```
