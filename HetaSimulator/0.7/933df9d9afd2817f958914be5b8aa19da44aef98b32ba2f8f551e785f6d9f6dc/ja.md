```
DataFrame(s::Simulation; 
  vars=observables(s), parameters_output::Vector{Symbol}=Symbol[], iter::Union{Int,Nothing}=nothing)
```

シミュレーション結果の型 `SimResult`、`MCResult` などを `DataFrame` に変換します。

例: `DataFrame(s)`

引数:

  * `s` : 型 [`SimResult`](@ref)、[`MCResult`](@ref) またはそれらを含む `Vector` のシミュレーション結果
  * `parameters_output` : `sim` または `mc` 関数に kwarg `parameters` として提供されたパラメータで、`DataFrame` に含めるべきもの。デフォルトは `empty`
  * `iter` : `DataFrame` に含めるべき `Int` イテレーション ID。デフォルトは `nothing`
