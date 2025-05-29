```
CategoricalTerm{C,T,N} <: AbstractTerm
```

Represents a categorical term, with a name and [`ContrastsMatrix`](@ref)

# Fields

  * `sym::Symbol`: The name of the variable
  * `contrasts::ContrastsMatrix`: A contrasts matrix that captures the unique values this variable takes on and how they are mapped onto numerical predictors.
