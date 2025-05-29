Particle represents a type that may be simulated using a transport Monte Carlo.  It must provide these methods:

```
position(el::Particle)::Position
previous(el::Particle)::Position
energy(el::Particle)::Float64
```

The position of the current and previous elastic scatter locations which are stored in that Particle type.

```
T(prev::Position, curr::Position, energy::Energy) where {T <: Particle }
T(el::T, 𝜆::Float64, 𝜃::Float64, 𝜑::Float64, ΔE::Float64) where {T <: Particle }
```

Two constructors: One to create a defined Particle and the other to create a new Particle based off another which is translated by `λ` at a scattering angle (`θ`, `ϕ`) which energy change of `ΔE`

```
transport(pc::T, mat::Material)::NTuple{4, Float64} where {T <: Particle }
```

A function that generates the values of ( `λ`, `θ`, `ϕ`, `ΔE`) for the specified `Particle` in the specified `Material`.
