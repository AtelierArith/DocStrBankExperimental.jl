```
uncertaintyparameter(od::ODProblem{D, T}, sol::NEOSolution{T, T},
    params::NEOParameters{T}) where {D, T <: Real}
```

小惑星センターの不確実性パラメータを返します。

## 引数

  * `od::ODProblem{D, T}`: 軌道決定問題。
  * `sol::NEOSolution{T, T}:` 参照軌道。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)を参照。

!!! reference
    https://www.minorplanetcenter.net/iau/info/UValue.html


!!! warning
    この関数は（グローバルな）`TaylorSeries`変数を変更します。

