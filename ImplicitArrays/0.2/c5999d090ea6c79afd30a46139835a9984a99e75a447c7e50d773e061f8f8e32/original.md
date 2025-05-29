```
InteractionMatrix{T, R, C, F <: InteractionFunction{R, C, T}} <: AbstractArray{T, 2}
```

Interaction matrix with elements of type `T`, generated from row elements of type `R`, column elements of type `C`, and an interaction function `F: R × C → T`.

# Constructors

```
InteractionMatrix(rowelems, colelems, interact)
InteractionMatrix{T}(rowelems, colelems, interact)
```

Create an interaction matrix for the given row and column element arrays as well as an interaction  function.

```
InteractionMatrix(rowelems, colelems, val)
```

Create an interaction matrix for the given (yet unused) row and column element arrays and a constant interaction function always returning `val`. In this form, the interaction matrix acts as a replacement for a two-dimensional [`FixedValueArray`](@ref).

# Examples

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
