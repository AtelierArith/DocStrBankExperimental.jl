```
Spin([M], M0, T1, T2, Δf, [pos]) <: AbstractSpin
```

Create an object that represents a single spin.

# Properties

  * `M::Magnetization = Magnetization(0, 0, M0)`: Magnetization vector
  * `M0::Real`: Equilibrium magnetization
  * `T1::Real`: Spin-lattice recovery time constant (ms)
  * `T2::Real`: Spin-spin recovery time constant (ms)
  * `Δf::Real`: Off-resonance frequency (Hz)
  * `pos::Position = Position(0, 0, 0)`: Spatial location (cm)
  * `N::Int = 1`: Number of compartments

# Examples

```jldoctest
julia> Spin(1, 1000, 100, 0, Position(1, 2, 3))
Spin{Float64}:
 M = Magnetization(0.0, 0.0, 1.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 0.0 Hz
 pos = Position(1.0, 2.0, 3.0) cm

julia> Spin(Magnetization(1, 2, 3), 1, 1000, 100, 0)
Spin{Float64}:
 M = Magnetization(1.0, 2.0, 3.0)
 M0 = 1.0
 T1 = 1000.0 ms
 T2 = 100.0 ms
 Δf = 0.0 Hz
 pos = Position(0.0, 0.0, 0.0) cm
```
