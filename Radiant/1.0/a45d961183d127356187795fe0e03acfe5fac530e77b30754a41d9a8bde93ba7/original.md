```
Material
```

Structure used to define a material and its properties.

# Mandatory field(s)

  * `name::String` : name (or identifier) of the Material structure.
  * `density::Float64` : density [in g/cm³].
  * `elements::Vector{String}` : vector of the element in the composition of the material.
  * `weight_fractions::Vector{Float64}` : vector of the weight fraction for each element in the composition of the material.

# Optional field(s) - with default values

  * `state_of_matter::String = "solid"` : state of the matter.
