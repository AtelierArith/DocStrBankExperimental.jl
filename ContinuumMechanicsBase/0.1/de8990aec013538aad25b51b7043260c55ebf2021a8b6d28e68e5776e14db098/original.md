```julia
predict(
    ψ::ContinuumMechanicsBase.AbstractMaterialModel,
    test::ContinuumMechanicsBase.AbstractMaterialTest,
    ps;
    kwargs...
) -> Hyperelastics.HyperelasticUniaxialTest

```

Fields:

  * `ψ`: Material Model
  * `test` or `tests`: A single test or vector of tests. This is used to predict the response of the model in comparison to the experimental data provided.
  * `ps`: Model parameters to be used.
