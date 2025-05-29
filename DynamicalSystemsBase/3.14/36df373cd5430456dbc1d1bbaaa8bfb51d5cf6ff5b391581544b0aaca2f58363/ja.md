```
current_parameters(ds::DynamicalSystem) → p
```

`ds`の現在のパラメータコンテナを返します。これは、パラメータ範囲にわたって`ds`を進化させる必要がある関数で変更されます。

[`initial_parameters`](@ref)、[`current_parameter`](@ref)、[`set_parameter!`](@ref)も参照してください。
