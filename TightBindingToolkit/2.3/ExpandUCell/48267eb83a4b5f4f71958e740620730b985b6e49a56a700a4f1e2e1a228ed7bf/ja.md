```julia
ChangePrimitives!(uc::UnitCell{T}, newPrimitives::Vector{Vector{Float64}})
```

与えられた `UnitCell` の原始ベクトルを変更します。サブ格子はそのままの状態を仮定します。それに応じて結合も変更されます。
