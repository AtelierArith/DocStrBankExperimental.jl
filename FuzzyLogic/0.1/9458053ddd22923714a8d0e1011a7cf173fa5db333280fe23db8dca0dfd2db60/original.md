```julia
struct SugenoFuzzySystem{And<:FuzzyLogic.AbstractAnd, Or<:FuzzyLogic.AbstractOr, R<:FuzzyLogic.AbstractRule} <: FuzzyLogic.AbstractFuzzySystem
```

Data structure representing a type-1 Sugeno fuzzy inference system. It can be created using the [`@sugfis`](@ref) macro. It can be called as a function to evaluate the system at a given input. The inputs should be given as keyword arguments.

  * `name::Symbol`: name of the system.
  * `inputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: input variables and corresponding domain.
  * `outputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: output variables and corresponding domain.
  * `rules::Vector{R} where R<:FuzzyLogic.AbstractRule`: inference rules.
  * `and::FuzzyLogic.AbstractAnd`: method used to compute conjuction in rules, default [`MinAnd`](@ref).
  * `or::FuzzyLogic.AbstractOr`: method used to compute disjunction in rules, default [`MaxOr`](@ref).
