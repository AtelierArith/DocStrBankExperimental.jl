```
struct MatrixGroupAction{T<:GroupType, F} <: AbstractGroupAction{T, F}
```

行列群の変数集合に対する群作用を表します。

# コンストラクタ

```julia
MatrixGroupAction(G::S, vectors::AbstractVector{<:AbstractVector{V}}) where {S<:AbstractGroup, V<:Variable}
```

# 例

```jldoctest
julia> @polyvar x[1:3] y[1:3];

julia> SO3 = LieGroup("SO", 3);

julia> MatrixGroupAction(SO3, [x, y])
MatrixGroupAction of SO(3)
 2 vectors under action: [x₁, x₂, x₃], [y₁, y₂, y₃]
```
