```
gaussiod(od::ODProblem{D, T}, params::NEOParameters{T}) where {D, T <: Real}
```

`od`に対してジェット輸送ガウス法を用いて予備軌道をフィットさせます。

[`gauss_method`](@ref)も参照してください。

## 引数

  * `od::ODProblem{D, T}`: 軌道決定問題。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)の`Gauss' Method Parameters`を参照してください。
