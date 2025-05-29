```
VarEffect(formula, covtype::T, coding) where T <: AbstractCovarianceType

VarEffect(formula, covtype::T; coding = nothing) where T <: AbstractCovarianceType

VarEffect(formula; coding = nothing)
```

Random/repeated effect.

  * `formula` from @covstr(ex) macros.
  * `covtype` - covariance type (SI, DIAG, CS, CSH, AR, ARH, ARMA, TOEP, TOEPH, TOEPP, TOEPHP)

!!! note
    Categorical factors are coded with `FullDummyCoding()` by default, use `coding` for other contrast codeing.


# Example

```julia
VarEffect(@covstr(1+factor|subject), CSH)

VarEffect(@covstr(1 + formulation|subject), CSH; coding = Dict(:formulation => StatsModels.DummyCoding()))
```
