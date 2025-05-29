```
Integral{T<:Union{Int,Tuple{Vararg{Int}}}} <: SpecialOperator
```

一般的な積分演算子。

フィールド:

  * `order :: T`

コンストラクタ:

  * `Integral(::Int)`
  * `Integral(::Tuple{Vararg{Int}})`
  * `Integral(order::Int...)`: `Integral(order)` と同等

参照: [`integrate`](@ref), [`integrate!`](@ref), [`project(::Integral, ::VectorSpace, ::VectorSpace)`](@ref) および [`project!(::LinearOperator, ::Integral)`](@ref).

# 例

```jldoctest
julia> Integral(1)
Integral{Int64}(1)

julia> Integral(1, 2)
Integral{Tuple{Int64, Int64}}((1, 2))
```
