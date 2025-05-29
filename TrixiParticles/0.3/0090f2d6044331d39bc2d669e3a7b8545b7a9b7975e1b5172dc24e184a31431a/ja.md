```
OpenBoundarySPHSystem(boundary_zone::BoundaryZone;
                      fluid_system::FluidSystem, buffer_size::Integer,
                      boundary_model,
                      reference_velocity=nothing,
                      reference_pressure=nothing,
                      reference_density=nothing)
```

入出力粒子のためのオープン境界システム。

# 引数

  * `boundary_zone`: [`BoundaryZone`](@ref)を参照してください。

# キーワード

  * `fluid_system`: 対応する流体システム
  * `boundary_model`: 境界モデル（[オープン境界モデル](@ref open_boundary_models)を参照）
  * `buffer_size`: バッファ粒子の数。
  * `reference_velocity`: 参照速度は、各粒子の座標と時間をその速度にマッピングする関数、$i$-番目の列に粒子$i$の速度を保持する配列、または一定の流体速度の場合、この速度を保持するベクトルです。
  * `reference_pressure`: 参照圧力は、各粒子の座標と時間をその圧力にマッピングする関数、各粒子の圧力を保持するベクトル、またはすべての粒子に対する一定の圧力のスカラーです。
  * `reference_density`: 参照密度は、各粒子の座標と時間をその密度にマッピングする関数、各粒子の密度を保持するベクトル、またはすべての粒子に対する一定の密度のスカラーです。

!!! note
    [`BoundaryModelTafuni()`](@ref)を使用する場合、参照値（`reference_velocity`、`reference_pressure`、`reference_density`）は`nothing`に設定することもできます。このモデルは、物理量を事前に割り当てるか、流体ドメインからバッファゾーン（流入および流出）への外挿を行うことを許可します（ゴーストノードを使用）。


!!! warning "実験的実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

