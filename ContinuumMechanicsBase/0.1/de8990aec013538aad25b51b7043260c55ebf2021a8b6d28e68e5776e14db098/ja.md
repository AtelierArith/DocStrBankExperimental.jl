```julia
predict(
    ψ::ContinuumMechanicsBase.AbstractMaterialModel,
    test::ContinuumMechanicsBase.AbstractMaterialTest,
    ps;
    kwargs...
) -> Hyperelastics.HyperelasticUniaxialTest

```

フィールド:

  * `ψ`: 材料モデル
  * `test` または `tests`: 単一のテストまたはテストのベクトル。これは、提供された実験データと比較してモデルの応答を予測するために使用されます。
  * `ps`: 使用されるモデルパラメータ。
