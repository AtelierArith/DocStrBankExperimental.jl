```
μ(
    material::Union{Element, Material, Matter},
    energies::Union{AbstractArray{<:Unitful.Energy}, T},
    a::Type{<:Attenuation} = DefaultAttenuation,
)
```

Calculate the linear attenuation coefficient for a given material.

The behavior of this function depends on the type of the first argument:

  * `Element`: The function multiplies the density of the element (`e.ρ`) with the mass attenuation coefficient (`μᵨ`) for the given energies and returns the result.
  * `Material`: The function multiplies the density of the material (`m.ρ`) with the mass attenuation coefficient (`μᵨ`) for the given energies and returns the result.
  * `Matter`: If a single energy value is given instead of an array, the function converts it into a single-element array and calculates the linear attenuation coefficient for that energy.

The `a` argument determines the type of attenuation to apply and defaults to `DefaultAttenuation`.
