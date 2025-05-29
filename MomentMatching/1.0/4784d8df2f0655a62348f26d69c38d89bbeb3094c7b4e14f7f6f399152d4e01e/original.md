```julia
Jtest(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    boot::MomentMatching.BootstrapResult,
    n::Integer
) -> DataFrames.DataFrame

```

Perform Hansen-Sargan test for overidentifying restrictions.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).
  * boot: Instance of BootstrapResult. See separate documentation [`BootstrapResult`](@ref).
  * n: Rescaling parameter for J-statistic (data size).
