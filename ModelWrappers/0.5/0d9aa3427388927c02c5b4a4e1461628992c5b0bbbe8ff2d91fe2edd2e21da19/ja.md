```julia
struct Objective{M<:ModelWrappers.ModelWrapper, D, T<:ModelWrappers.Tagged, F<:AbstractFloat} <: BaytesCore.AbstractObjective
```

制約のない 'θᵤ' で 'ℓfunc' と勾配を計算するファンクタ、最終的なヤコビ行列の調整を含む。

# フィールド

  * `model::ModelWrappers.ModelWrapper`
  * `data::Any`
  * `tagged::ModelWrappers.Tagged`
  * `temperature::AbstractFloat`
