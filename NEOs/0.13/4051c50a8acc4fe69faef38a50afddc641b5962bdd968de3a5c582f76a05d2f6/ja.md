```
orbitdetermination(od::ODProblem{D, T}, sol::NEOSolution{T, T},
    params::NEOParameters{T}) where {D, T <: Real}
```

`sol`を初期条件として使用して、`od`に最小二乗軌道をフィットさせます。

## 引数

  * `od::ODProblem{D, T}`: 軌道決定問題。
  * `sol::NEOSolution{T, T}:` 仮の軌道。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)を参照してください。

!!! warning
    この関数は（グローバルな）`TaylorSeries`変数を変更します。

