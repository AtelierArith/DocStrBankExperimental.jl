```
QuasiNewtonState <: AbstractManoptSolverState
```

これらのQuasi Newton [`AbstractManoptSolverState`](@ref) は、任意の準ニュートンベースのメソッドを表し、方向の更新ルールと共に使用できます。

# フィールド

  * `p`                             現在の反復点、マニフォールド上の点
  * `X`                             現在の勾配
  * `sk`                            現在のステップ
  * `yk`                            現在の勾配の差
  * `direction_update`              [`AbstractQuasiNewtonDirectionUpdate`](@ref) ルール。
  * `nondescent_direction_behavior` 非降下方向を扱う方法を指定する `Symbol`。
  * `retraction_method`             `AbstractRetractionMethod`
  * `stepsize`                      [`Stepsize`](@ref)
  * `stop`                          [`StoppingCriterion`](@ref)

内部使用のために

  * `p_old`                      最後の反復点
  * `η`                          現在の更新方向
  * `X_old`                      最後の勾配
  * `nondescent_direction_value` 降下方向をチェックする際の最後の内積からの値

# コンストラクタ

```
QuasiNewtonState(
    M::AbstractManifold,
    x;
    initial_vector=zero_vector(M,x),
    direction_update::D=QuasiNewtonLimitedMemoryDirectionUpdate(M, x, InverseBFGS(), 20;
        vector_transport_method=vector_transport_method,
    )
    stopping_criterion=StopAfterIteration(1000) | StopWhenGradientNormLess(1e-6),
    retraction_method::RM=default_retraction_method(M, typeof(p)),
    vector_transport_method::VTM=default_vector_transport_method(M, typeof(p)),
    stepsize=default_stepsize(M; QuasiNewtonState)
)
```

# 参照

[`quasi_Newton`](@ref)
