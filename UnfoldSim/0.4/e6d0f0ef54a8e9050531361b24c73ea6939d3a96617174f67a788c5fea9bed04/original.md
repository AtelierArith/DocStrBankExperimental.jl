```
MixedModelComponent <: AbstractComponent
```

A component that adds a hierarchical relation between parameters according to a Linear Mixed Model (LMM) defined via `MixedModels.jl`.

All fields can be named. Works best with [`MultiSubjectDesign`](@ref).

# Fields

  * `basis::Any`: an object, if accessed, provides a 'basis function', e.g. `hanning(40)::Vector`, this defines the response at a single event. It will be weighted by the model prediction. Future versions will allow for functions, as of v0.3 this is restricted to array-like objects
  * `formula::Any`: Formula-object in the style of MixedModels.jl e.g. `@formula 0 ~ 1 + cond + (1|subject)`. The left-hand side is ignored.
  * `β::Vector` Vector of betas (fixed effects), must fit the formula.
  * `σs::Dict` Dict of random effect variances, e.g. `Dict(:subject => [0.5, 0.4])` or to specify correlation matrix `Dict(:subject=>[0.5,0.4,I(2,2)],...)`. Technically, this will be passed to the MixedModels.jl `create_re` function, which creates the θ matrices.
  * `contrasts::Dict` (optional): Dict in the style of MixedModels.jl. Determines which coding scheme to use for which categorical variables. Default is empty which corresponds to dummy coding. For more information see [https://juliastats.org/StatsModels.jl/stable/contrasts](https://juliastats.org/StatsModels.jl/stable/contrasts).

# Examples

```julia-repl
julia> MixedModelComponent(;
           basis = hanning(40),
           formula = @formula(0 ~ 1 + cond + (1 + cond|subject)),
           β = [1., 2.],
           σs= Dict(:subject => [0.5, 0.4]),
           contrasts=Dict(:cond => EffectsCoding())
       )
MixedModelComponent
  basis: Array{Float64}((40,)) [0.0, 0.006474868681043577, 0.02573177902642726, 0.0572719871733951, 0.10027861829824952, 0.1536378232452003, 0.21596762663442215, 0.28565371929847283, 0.3608912680417737, 0.43973165987233853  …  0.43973165987233853, 0.3608912680417737, 0.28565371929847283, 0.21596762663442215, 0.1536378232452003, 0.10027861829824952, 0.0572719871733951, 0.02573177902642726, 0.006474868681043577, 0.0]
  formula: StatsModels.FormulaTerm{StatsModels.ConstantTerm{Int64}, Tuple{StatsModels.ConstantTerm{Int64}, StatsModels.Term, StatsModels.FunctionTerm{typeof(|), Vector{StatsModels.AbstractTerm}}}}
  β: Array{Float64}((2,)) [1.0, 2.0]
  σs: Dict{Symbol, Vector{Float64}}
  contrasts: Dict{Symbol, EffectsCoding}
```

See also [`LinearModelComponent`](@ref), [`MultichannelComponent`](@ref).
