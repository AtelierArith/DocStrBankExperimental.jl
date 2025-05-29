```
DiffusiveCFL(Δt)
```

時間ステップ `Δt` または `TimeStepWizard` に関連する拡散コーラン・フリードリッヒス・ルビー (CFL) 数を計算するためのオブジェクトを返します。また、`model.closure` に関連するセルを横断する拡散の時間スケールも返します。拡散CFL、例えば粘性の場合は $ν Δt / Δx²$ です。

粘性およびすべてのトレーサー拡散率の中での最大拡散CFL数が返されます。

# 例

```jldoctest
julia> using Oceananigans

julia> model = NonhydrostaticModel(grid = RectilinearGrid(size=(16, 16, 16), extent=(1, 1, 1)),
                                   closure = ScalarDiffusivity(; ν = 1e-2));

julia> Δt = 0.1;

julia> dcfl = DiffusiveCFL(Δt);

julia> dcfl(model)
0.256
```
