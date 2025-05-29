```
Derivative{T<:Union{Int,Tuple{Vararg{Int}}}} <: SpecialOperator
```

一般的な導関数演算子。

フィールド:

  * `order :: T`

コンストラクタ:

  * `Derivative(::Int)`
  * `Derivative(::Tuple{Vararg{Int}})`
  * `Derivative(order::Int...)`: `Derivative(order)` と同等

参照: [`differentiate`](@ref), [`differentiate!`](@ref), [`project(::Derivative, ::VectorSpace, ::VectorSpace)`](@ref) および [`project!(::LinearOperator, ::Derivative)`](@ref)。

# 例

```jldoctest
julia> Derivative(1)
Derivative{Int64}(1)

julia> Derivative(1, 2)
Derivative{Tuple{Int64, Int64}}((1, 2))
```
