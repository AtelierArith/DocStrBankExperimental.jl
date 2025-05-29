```
TimeStepWizard([FT=Float64;]
               cfl = 0.2,
               diffusive_cfl = Inf,
               max_change = 1.1,
               min_change = 0.5,
               max_Δt = Inf,
               min_Δt = 0.0,
               cell_advection_timescale = cell_advection_timescale,
               cell_diffusion_timescale = infinite_diffusion_timescale)
```

シミュレーションの時間ステップを、指定された目標値に合わせて調整するコールバック関数で、対流および拡散のクーラン数（CFL）(`cfl` および `diffusive_cfl`）に従い、以下の制限に従います。

```julia
max(min_Δt, min_change * last_Δt) ≤ new_Δt ≤ min(max_Δt, max_change * last_Δt)
```

ここで `new_Δt` は `TimeStepWizard` によって計算された新しい時間ステップです。

CFL数の詳細については、[wikipediaのエントリ](https://en.wikipedia.org/wiki/Courant%E2%80%93Friedrichs%E2%80%93Lewy_condition)を参照してください。

# 例

`TimeStepWizard` を使用するには、それを [`Callback`](@ref) に挿入し、次に `Callback` を `Simulation` に追加します。

```julia
julia> simulation = Simulation(model, Δt=0.9, stop_iteration=100)

julia> wizard = TimeStepWizard(cfl=0.2)

julia> simulation.callbacks[:wizard] = Callback(wizard, IterationInterval(4))
```

その後、`run!(simulation)` が呼び出されると、時間ステップ `simulation.Δt` は4回の反復ごとに更新されます。

（`:wizard` という名前は重要ではありません。）
