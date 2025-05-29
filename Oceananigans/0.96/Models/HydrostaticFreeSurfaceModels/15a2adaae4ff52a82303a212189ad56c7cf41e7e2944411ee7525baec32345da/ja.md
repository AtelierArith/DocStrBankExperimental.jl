```
PrescribedVelocityFields(; u = ZeroField(),
                           v = ZeroField(),
                           w = ZeroField(),
                           parameters = nothing)
```

は、指定された関数 `u`、`v`、および `w` を持つ `PrescribedVelocityFields` を構築します。

`parameters` が `isnothing` の場合、`u, v, w` は次のシグネチャで呼び出されます。

```
u(x, y, z, t) = # 興味深い何か
```

`!isnothing(parameters)` の場合、`u, v, w` は次のシグネチャで呼び出されます。

```
u(x, y, z, t, parameters) = # パラメータ化され、興味深い何か
```

`HydrostaticFreeSurfaceModel` のコンストラクタでは、関数 `u, v, w` は `FunctionField` にラップされ、モデルの `grid` と `clock` に関連付けられます。
