```julia
calcFactorResidualTemporary(
    fct,
    varTypes,
    measurement,
    pts;
    tfg,
    _blockRecursion,
    doTime
)

```

Evaluate the residual function for a single sample.

Notes

  * Binary factors only at this stage, and `multihypo` does not have to be considered in this test
  * Assumes calculation is for a single particle, so `meas::Tuple{Z,other}` is only a single particles value.

Example

```julia
residual = calcFactorResidualTemporary(Pose2Pose2(...), (RoME.Pose2,RoME.Pose2), (z_i,), (x1, x2))
```

Related

[`calcFactorResidual`](@ref), [`CalcResidual`](@ref), [`_evalFactorTemporary!`](@ref), [`approxConvBelief`](@ref), [`_buildGraphByFactorAndTypes!`](@ref)
