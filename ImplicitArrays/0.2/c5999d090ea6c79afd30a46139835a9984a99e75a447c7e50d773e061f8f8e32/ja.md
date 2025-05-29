```
InteractionMatrix{T, R, C, F <: InteractionFunction{R, C, T}} <: AbstractArray{T, 2}
```

要素の型 `T` を持つインタラクション行列で、行要素の型 `R`、列要素の型 `C`、およびインタラクション関数 `F: R × C → T` から生成されます。

# コンストラクタ

```
InteractionMatrix(rowelems, colelems, interact)
InteractionMatrix{T}(rowelems, colelems, interact)
```

指定された行および列要素配列とインタラクション関数に対してインタラクション行列を作成します。

```
InteractionMatrix(rowelems, colelems, val)
```

指定された（まだ使用されていない）行および列要素配列と、常に `val` を返す定数インタラクション関数に対してインタラクション行列を作成します。この形式では、インタラクション行列は二次元の [`FixedValueArray`](@ref) の代わりとして機能します。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> InteractionMatrix{Int64}([1, 2, 3], [10, 20, 30], +)
3×3 InteractionMatrix{Int64, Int64, Int64, GenericInteractionFunction{Int64, Int64, Int64}}:
 11  21  31
 12  22  32
 13  23  33

julia> InteractionMatrix([1, 2, 3], [10, 20, 30], 42)
3×3 InteractionMatrix{Int64, Int64, Int64, ConstInteractionFunction{Int64, Int64, Int64}}:
 42  42  42
 42  42  42
 42  42  42

julia> struct DivFun <: InteractionFunction{Int, Int, Float64} end

julia> (::DivFun)(x::Int, y::Int) = x / y

julia> InteractionMatrix([10, 20, 30], [5, 2, 1], DivFun())
3×3 InteractionMatrix{Float64, Int64, Int64, DivFun}:
 2.0   5.0  10.0
 4.0  10.0  20.0
 6.0  15.0  30.0
```
