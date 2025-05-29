```
Scale{T<:Union{Number,Tuple{Vararg{Number}}}} <: SpecialOperator
```

汎用スケール演算子。

フィールド:

  * `value :: T`

コンストラクタ:

  * `Scale(::Number)`
  * `Scale(::Tuple{Vararg{Number}})`
  * `Scale(value::Number...)`: `Scale(value)` と同等

参照: [`scale`](@ref), [`scale!`](@ref), [`project(::Scale, ::VectorSpace, ::VectorSpace)`](@ref) および [`project!(::LinearOperator, ::Scale)`](@ref)。

# 例

```jldoctest
julia> Scale(1.0)
Scale{Float64}(1.0)

julia> Scale(1.0, 2.0)
Scale{Tuple{Float64, Float64}}((1.0, 2.0))
```
