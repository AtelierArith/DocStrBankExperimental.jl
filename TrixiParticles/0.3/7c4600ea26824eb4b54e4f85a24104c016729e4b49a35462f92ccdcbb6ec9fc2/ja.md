```
Semidiscretization(systems...; neighborhood_search=GridNeighborhoodSearch{NDIMS}())
```

セミ離散化は、渡されたシステムを1つのシミュレーションに結合します。

# 引数

  * `systems`: このセミ離散化で結合されるシステム

# キーワード

  * `neighborhood_search`:    シミュレーションで使用される近傍探索。                           デフォルトでは、[`GridNeighborhoodSearch`](@ref)が使用されます。                           すべての粒子をループするには`nothing`を使用します（近傍探索なし）。                           他の近傍探索の実装を使用するには、近傍探索のテンプレートを渡します。                           詳細については、[`copy_neighborhood_search`](@ref)                           および以下の例を参照してください。                           周期的な領域を使用するには、近傍探索に[`PeriodicBox`](@ref)を渡します。
  * `threaded_nhs_update=true`:   近傍探索の更新におけるスレッド並列化を無効にするために使用できます。                               これは、粒子の順序変更により、異なるスレッド数のシミュレーション間での変動の                               最大の原因の1つとなる可能性があります。

# 例

```jldoctest; output = false, setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), sol=nothing); ref_system = fluid_system)
semi = Semidiscretization(fluid_system, boundary_system)

semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=GridNeighborhoodSearch{2}(update_strategy=SerialUpdate()))

periodic_box = PeriodicBox(min_corner = [0.0, 0.0], max_corner = [1.0, 1.0])
semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=GridNeighborhoodSearch{2}(; periodic_box))

semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=PrecomputedNeighborhoodSearch{2}())

semi = Semidiscretization(fluid_system, boundary_system,
                          neighborhood_search=nothing)

# 出力
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ Semidiscretization                                                                               │
│ ══════════════════                                                                               │
│ #空間次元: ………………………… 2                                                                │
│ #システム: ……………………………………………………… 2                                                                │
│ 近傍探索: ………………………… TrivialNeighborhoodSearch                                        │
│ 合計 #粒子: ………………………………… 636                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
