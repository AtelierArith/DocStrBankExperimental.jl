```
RobustLinearModel
```

ロバスト線形モデルの表現

## フィールド

  * `resp`: [`RobustLinResp`](@ref) 構造体。
  * `pred`: [`DensePredChol`](@ref)、[`SparsePredChol`](@ref)、[`DensePredCG`](@ref)、[`SparsePredCG`](@ref) または [`RidgePred`](@ref) 型の予測子構造体。
  * `formula`: `FormulaTerm` オブジェクトまたは `nothing`
  * `fitdispersion`: true の場合、分散が推定され、それ以外の場合は固定される
  * `fitted`: true の場合、モデルはすでにフィッティングされている
