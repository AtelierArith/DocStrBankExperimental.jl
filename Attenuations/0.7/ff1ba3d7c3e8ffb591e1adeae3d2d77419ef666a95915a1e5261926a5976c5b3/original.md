```
μᵨ(
    material::Union{Matter, Element, Compound, Mixture, Material},
    energies::AbstractArray{<:Unitful.Energy},
    a::Type{A} = DefaultAttenuation,
)
```

Calculate the mass attenuation coefficient for a given material.

The behavior of this function depends on the type of the first argument:

  * `Matter`: the `energies` array is transformed into a single energy value.
  * `Element`: The function uses the atomic number of the element (`e.Z`) to create a request body for the XCOM service, and returns the mass attenuation coefficient in cm²/g for the given energies.
  * `Compound`: Similar to `Element`, but uses the compound's formula instead of the atomic number.
  * `Mixture`: The function creates a request body with a string representation of the mixture's formulae and uses the XCOM service to calculate the mass attenuation coefficient for the given energies.
  * `Material`: The function converts the material's composition into a `Mixture` and then proceeds as in the `Mixture` case.

The `a` argument determines the type of attenuation to apply and defaults to `DefaultAttenuation`.
