```
create_modeldata(model::Model [; arrays_eltype=Float64]) -> modeldata::ModelData
```

モデル変数のための新しい [`ModelData`](@ref) 構造体を、データ配列の要素型 `arrays_eltype` で作成します。
