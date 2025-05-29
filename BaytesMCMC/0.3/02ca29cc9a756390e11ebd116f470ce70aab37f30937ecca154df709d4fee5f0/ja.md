```julia
struct GeneralizedTurnStatistic{T}
```

転換点の特定のための統計。Betancourt (2017, 付録) および [https://discourse.mc-stan.org/t/nuts-misses-u-turns-runs-in-circles-until-max-treedepth/9727/](https://discourse.mc-stan.org/t/nuts-misses-u-turns-runs-in-circles-until-max-treedepth/9727/) での改善に関するその後の議論を参照してください。モーメンタ `p₋` と `p₊` は、ターン統計を組み合わせる際に `ρ` に加えられるように保持されます。ターン検出は常に [`combine_turn_statistics`](@ref) によって行われ、ターンが発生した場合は `nothing` を返します。`GeneralizedTurnStatistic` は常に *回転していない* 軌道（または概念が適用されない葉ノード）に対応する必要があります。

# フィールド

  * `ρ₋::Any`: 軌道の左端でのモーメンタ
  * `ρ♯₋::Any`: 軌道の左端での p♯
  * `ρ₊::Any`: 軌道の右端でのモーメンタ
  * `ρ♯₊::Any`: 軌道の右端での p♯
  * `ρₛ::Any`: 軌道に沿ったモーメンタの合計
