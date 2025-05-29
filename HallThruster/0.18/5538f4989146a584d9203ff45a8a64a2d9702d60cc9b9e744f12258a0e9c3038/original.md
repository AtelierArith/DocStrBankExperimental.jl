```julia
struct Gas
```

A chemical element in the gaseous state. Container for element properties used in fluid computations.

# Fields

  * `name::String`: Full name of gas (i.e. Xenon)
  * `short_name::String`: Short name/symbol (i.e. Xe for Xenon)
  * `γ::Float64`: Specific heat ratio / adiabatic index
  * `M::Float64`: Molar mass (grams/mol) or atomic mass units
  * `m::Float64`: Mass of atom in kg
  * `cp::Float64`: Specific heat at constant pressure
  * `cv::Float64`: Specific heat at constant volume
  * `R::Float64`: Gas constant
