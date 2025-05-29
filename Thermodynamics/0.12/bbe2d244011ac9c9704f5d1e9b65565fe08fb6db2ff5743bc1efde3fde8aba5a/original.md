```
internal_energy(ρ::FT, ρe::FT, ρu::AbstractVector{FT}, e_pot::FT)
```

The internal energy per unit mass, given

  * `ρ` (moist-)air density
  * `ρe` total energy per unit volume
  * `ρu` momentum vector
  * `e_pot` potential energy (e.g., gravitational) per unit mass
