```
LinearModelComponent <: AbstractComponent
```

A multiple regression component for one subject.

All fields can be named. Works best with [`SingleSubjectDesign`](@ref).

# Fields

  * `basis::Any`: an object, if accessed, provides a 'basis function', e.g. `hanning(40)::Vector`, this defines the response at a single event. It will be weighted by the model prediction. Future versions will allow for functions, as of v0.3 this is restricted to array-like objects
  * `formula::Any`: StatsModels `formula` object, e.g.  `@formula 0 ~ 1 + cond` (left-hand side must be 0).
  * `β::Vector` Vector of betas/coefficients, must fit the formula.
  * `contrasts::Dict` (optional): Determines which coding scheme to use for which categorical variables. Default is empty which corresponds to dummy coding.    For more information see [https://juliastats.org/StatsModels.jl/stable/contrasts](https://juliastats.org/StatsModels.jl/stable/contrasts).

# Examples

```julia-repl
julia> LinearModelComponent(;
           basis = hanning(40),
           formula = @formula(0 ~ 1 + cond),
           β = [1., 2.],
           contrasts = Dict(:cond => EffectsCoding())
       )
LinearModelComponent
  basis: Array{Float64}((40,)) [0.0, 0.006474868681043577, 0.02573177902642726, 0.0572719871733951, 0.10027861829824952, 0.1536378232452003, 0.21596762663442215, 0.28565371929847283, 0.3608912680417737, 0.43973165987233853  …  0.43973165987233853, 0.3608912680417737, 0.28565371929847283, 0.21596762663442215, 0.1536378232452003, 0.10027861829824952, 0.0572719871733951, 0.02573177902642726, 0.006474868681043577, 0.0]
  formula: StatsModels.FormulaTerm{StatsModels.ConstantTerm{Int64}, Tuple{StatsModels.ConstantTerm{Int64}, StatsModels.Term}}
  β: Array{Float64}((2,)) [1.0, 2.0]
  contrasts: Dict{Symbol, EffectsCoding}
```

See also [`MixedModelComponent`](@ref), [`MultichannelComponent`](@ref).
