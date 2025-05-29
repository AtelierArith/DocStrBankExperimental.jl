```
Shift{T<:Union{Number,Tuple{Vararg{Number}}}} <: SpecialOperator
```

汎用シフト演算子。

フィールド:

  * `value :: T`

コンストラクタ:

  * `Shift(::Number)`
  * `Shift(::Tuple{Vararg{Number}})`
  * `Shift(value::Number...)`: `Shift(value)` と同等

参照: [`shift`](@ref), [`shift!`](@ref), [`project(::Shift, ::VectorSpace, ::VectorSpace)`](@ref) および [`project!(::LinearOperator, ::Shift)`](@ref)。

# 例

```jldoctest
julia> Shift(1.0)
Shift{Float64}(1.0)

julia> Shift(1.0, 2.0)
Shift{Tuple{Float64, Float64}}((1.0, 2.0))
```
