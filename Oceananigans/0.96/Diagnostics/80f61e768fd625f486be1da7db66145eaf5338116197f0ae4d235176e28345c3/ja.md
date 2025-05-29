```
AdvectiveCFL(Δt)
```

時間ステップ `Δt` または `TimeStepWizard` に関連するクーラン-フリードリッヒス-ルーウィ (CFL) 数を計算するためのオブジェクトを返します。輸送におけるCFLは、例えば、$U Δt / Δx$ です。

# 例

```jldoctest
julia> using Oceananigans

julia> model = NonhydrostaticModel(grid = RectilinearGrid(size=(16, 16, 16), extent=(8, 8, 8)));

julia> Δt = 1.0;

julia> cfl = AdvectiveCFL(Δt);

julia> model.velocities.u .= π;

julia> cfl(model)
6.283185307179586
```
