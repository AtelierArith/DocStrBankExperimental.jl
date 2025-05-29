```
Isotopomers{T <: AbstractChemical} <: AbstractChemical
```

Chemicals differed from isotopic replacement location.

# Fields

  * `parent`: shared chemical structure of isotopomers prior to isotopic replacement.
  * `isotopes`: `Vector{Pair{String, Int}}`. Isotopes-number pairs of isotopic replacement.

# Constructors

  * `Isotopomers(parent::AbstractChemical, fullformula::String)`
  * `Isotopomers(parent::AbstractChemical, fullelements::Dictionary)`
