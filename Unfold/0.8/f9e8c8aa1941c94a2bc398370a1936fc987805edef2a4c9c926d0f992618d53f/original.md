```julia
designmatrix(
    unfoldmodeltype,
    f,
    tbl,
    basisfunction;
    contrasts,
    eventname,
    kwargs...
)

```

designmatrix(type, f, tbl; kwargs...) Return a *DesignMatrix* used to fit the models.

# Arguments

  * type::UnfoldModel
  * f::FormulaTerm: Formula to be used in this designmatrix
  * tbl: Events (usually a data frame) to be modelled
  * basisfunction::BasisFunction: basisfunction to be used in modeling (if specified)
  * contrasts::Dict: (optional) contrast to be applied to formula
  * eventfields::Array: (optional) Array of symbols which are passed to basisfunction event-wise.

First field of array always defines eventonset in samples. Default is [:latency]

# Examples

```julia-repl
julia>  designmatrix(UnfoldLinearModelContinuousTime,Dict(Any=>(f,basisfunction1),tbl)
```
