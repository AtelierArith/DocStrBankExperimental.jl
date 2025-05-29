```
BoundaryCondition(classification::AbstractBoundaryConditionClassification, condition::Function;
                  parameters = nothing,
                  discrete_form = false,
                  field_dependencies=())
```

境界条件のタイプ `classification` を関数境界 `condition` で構築します。

デフォルトでは、関数境界 `condition` は '連続形' `condition(ξ, η, t)` を持つと仮定され、ここで `t` は時間であり、`ξ` と `η` は境界に沿って変化します。特に：

  * `x`-境界では、`condition(y, z, t)`。
  * `y`-境界では、`condition(x, z, t)`。
  * `z`-境界では、`condition(x, y, t)`。

`parameters` が `nothing` でない場合、関数境界条件は `func(ξ, η, t, parameters)` の形を持ち、ここで `ξ` と `η` は上記のように境界に沿って変化する空間座標です。

`discrete_form = true` の場合、関数 `condition` は "離散形" を持つと仮定されます。

```
condition(i, j, grid, clock, model_fields)
```

ここで `i` と `j` は境界に沿って変化するインデックスです。`discrete_form = true` で `parameters` が `nothing` でない場合、関数 `condition` は次のように呼び出されます。

```
condition(i, j, grid, clock, model_fields, parameters)
```
