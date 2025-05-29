```
AnovaResult{M, T, N}
```

Returned object of `anova`.

  * `M` is `NestedModels` or `FullModel`.
  * `T` is a subtype of `GoodnessOfFit`; either `FTest` or `LRT`.
  * `N` is the length of parameters.

# Fields

  * `anovamodel`: [`NestedModels`](@ref), [`MixedAovModels`](@ref), or [`FullModel`](@ref).
  * `dof`: degrees of freedom of models or predictors.
  * `deviance`: deviance(s) for calculating test statistics. See [`deviance`](@ref) for more details.
  * `teststat`: value(s) of test statiscics.
  * `pval`: p-value(s) of test statiscics.
  * `otherstat`: `NamedTuple` contained extra statistics.

# Constructor

```
AnovaResult(
        anovamodel::M,
        ::Type{T},
        dof::NTuple{N, Int},
        deviance::NTuple{N, Float64},
        teststat::NTuple{N, Float64},
        pval::NTuple{N, Float64},
        otherstat::NamedTuple
) where {N, M <: AnovaModel{<: RegressionModel, N}, T <: GoodnessOfFit}
```
