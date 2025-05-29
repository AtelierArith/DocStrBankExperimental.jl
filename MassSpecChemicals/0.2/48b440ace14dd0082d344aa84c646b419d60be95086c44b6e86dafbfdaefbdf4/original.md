```
Chemical <: AbstractChemical
```

Unstructured chemical type with its name, formula, and additional attributes.

# Fields

  * `name`: a unique chemical name (`String`).
  * `formula`: chemical formula (`String`).
  * `attr`: additional attributes (`Vector{Pair{Symbol, Any}}`); the pairs repressent attribute names and values.

# Constructors

  * `Chemical(name::AbstractString, formula::AbstractString; kwargs_as_attr_pairs...)`
