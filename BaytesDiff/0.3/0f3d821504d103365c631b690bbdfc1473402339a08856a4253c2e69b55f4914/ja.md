```julia
struct ObjectiveError <: Exception
```

評価できなかった対数密度の制約された空間内のパラメータを格納します。

# フィールド

  * `msg::String`
  * `ℓθᵤ::Real`
  * `θ::NamedTuple`
  * `θᵤ::AbstractVector`
