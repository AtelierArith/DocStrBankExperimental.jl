```
Field(operand::OperationOrFunctionField;
      data = nothing,
      indices = indices(operand),
      boundary_conditions = FieldBoundaryConditions(operand.grid, location(operand)),
      recompute_safely = true)
```

フィールド `f` を返します。ここで `f.data` は `compute!(f)` を呼び出すことによって `f.operand` から計算されます。

# キーワード引数

`data` (`AbstractArray`): 計算結果を格納するためのオフセット配列または CuArray。                           `total_size(location(operand), grid)` を持つ必要があります。

`boundary_conditions` (`FieldBoundaryConditions`): `f` の境界条件。

`recompute_safely` (`Bool`): `f` が `AbstractOperation` または `FunctionField` を介して別の計算内にネストされている場合に、常に `f` を「再計算」するかどうか。                              `data` が提供されていない場合、`recompute_safely=false` となり、                              再計算は *回避されます*。`data` が提供されている場合、                              デフォルトで `recompute_safely = true` となります。
