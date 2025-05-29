```
abstract type TransientFEOperator <: GridapType end
```

残差の形に対応する `FEOperator` の一時的なバージョン

```
residual(t, u, v) = 0,
```

ここで `residual` は `v` に対して線形です。`u` の時間微分は `∂t` 演算子を使用することで含めることができます。

# 重要

現時点では、残差とヤコビアンは `TransientFEOperator` 上で直接計算することはできません。これらは対応する代数演算子である `ODEOperator` 上で評価する必要があります。そのため、`TransientFEOperator` は厳密には `FEOperator` のサブタイプではなく、むしろ `FEOperator` と `ODEOperator` の交差点に位置しています。これは `ODEOperator` がベクトルで動作し、定数形式を活用するように最適化されているためです。

# 必須

  * [`get_test(tfeop)`](@ref)
  * [`get_trial(tfeop)`](@ref)
  * [`get_order(tfeop)`](@ref)
  * [`get_res(tfeop::TransientFEOperator)`](@ref)
  * [`get_jacs(tfeop::TransientFEOperator)`](@ref)
  * [`get_forms(tfeop::TransientFEOperator)`](@ref)
  * [`get_assembler(tfeop)`](@ref)

# 任意

  * [`get_algebraic_operator(tfeop)`](@ref)
  * [`get_num_forms(tfeop::TransientFEOperator)`](@ref)
  * [`is_form_constant(tfeop, k)`](@ref)
  * [`allocate_tfeopcache(tfeop)`](@ref)
  * [`update_tfeopcache!(tfeopcache, tfeop, t)`](@ref)
