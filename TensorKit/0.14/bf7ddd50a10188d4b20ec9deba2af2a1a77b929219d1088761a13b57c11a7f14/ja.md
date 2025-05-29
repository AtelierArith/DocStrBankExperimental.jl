```
struct TensorMap{T, S<:IndexSpace, N₁, N₂, A<:DenseVector{T}} <: AbstractTensorMap{T, S, N₁, N₂}
```

テンソルカテゴリにおけるテンソルマップ（モルフィズム）を表すための[`AbstractTensorMap`](@ref)の特定のサブタイプであり、データは密なベクトルに格納されます。
