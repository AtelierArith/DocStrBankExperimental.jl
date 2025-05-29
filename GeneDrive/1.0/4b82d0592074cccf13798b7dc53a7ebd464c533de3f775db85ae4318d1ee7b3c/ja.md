```
mutable struct Density{D <: DensityDependence}
    model::Type{D}
    param::Float64
end
```

密度依存モデルのデータ。

# 引数

  * `model::Type{D}`: ユーザーが選択した密度依存の定式化。`LogisticDensity`、`LinearDensity`、および `NoDensity` が含まれます。
  * `param::Float64`: `init` 関数によって内部的に計算されます。
