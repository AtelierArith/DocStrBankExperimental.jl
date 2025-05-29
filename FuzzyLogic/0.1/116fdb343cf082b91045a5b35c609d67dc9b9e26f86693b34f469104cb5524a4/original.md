```julia
struct MamdaniFuzzySystem{And<:FuzzyLogic.AbstractAnd, Or<:FuzzyLogic.AbstractOr, Impl<:FuzzyLogic.AbstractImplication, Aggr<:FuzzyLogic.AbstractAggregator, Defuzz<:FuzzyLogic.AbstractDefuzzifier, R<:FuzzyLogic.AbstractRule} <: FuzzyLogic.AbstractFuzzySystem
```

Data structure representing a type-1 Mamdani fuzzy inference system. It can be created using the [`@mamfis`](@ref) macro. It can be called as a function to evaluate the system at a given input. The inputs should be given as keyword arguments.

  * `name::Symbol`: name of the system.
  * `inputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: input variables and corresponding domain.
  * `outputs::Dictionaries.Dictionary{Symbol, FuzzyLogic.Variable}`: output variables and corresponding domain.
  * `rules::Vector{R} where R<:FuzzyLogic.AbstractRule`: inference rules.
  * `and::FuzzyLogic.AbstractAnd`: method used to compute conjuction in rules, default [`MinAnd`](@ref).
  * `or::FuzzyLogic.AbstractOr`: method used to compute disjunction in rules, default [`MaxOr`](@ref).
  * `implication::FuzzyLogic.AbstractImplication`: method used to compute implication in rules, default [`MinImplication`](@ref)
  * `aggregator::FuzzyLogic.AbstractAggregator`: method used to aggregate fuzzy outputs, default [`MaxAggregator`](@ref).
  * `defuzzifier::FuzzyLogic.AbstractDefuzzifier`: method used to defuzzify the result, default [`CentroidDefuzzifier`](@ref).

# Extended help

### Example

```jldoctest; filter=r"Dictionaries\."
fis = @mamfis function tipper(service, food)::tip
    service := begin
      domain = 0:10
      poor = GaussianMF(0.0, 1.5)
      good = GaussianMF(5.0, 1.5)
      excellent = GaussianMF(10.0, 1.5)
    end

    food := begin
      domain = 0:10
      rancid = TrapezoidalMF(-2, 0, 1, 3)
      delicious = TrapezoidalMF(7, 9, 10, 12)
    end

    tip := begin
      domain = 0:30
      cheap = TriangularMF(0, 5, 10)
      average = TriangularMF(10, 15, 20)
      generous = TriangularMF(20, 25, 30)
    end

    service == poor || food == rancid --> tip == cheap
    service == good --> tip == average
    service == excellent || food == delicious --> tip == generous
end

fis(service=1, food=2)

# output

1-element Dictionaries.Dictionary{Symbol, Float64}
 :tip │ 5.558585929783786
```
