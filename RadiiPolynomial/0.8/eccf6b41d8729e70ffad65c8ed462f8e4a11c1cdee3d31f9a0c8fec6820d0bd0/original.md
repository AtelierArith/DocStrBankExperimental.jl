```
Derivative{T<:Union{Int,Tuple{Vararg{Int}}}} <: SpecialOperator
```

Generic derivative operator.

Field:

  * `order :: T`

Constructors:

  * `Derivative(::Int)`
  * `Derivative(::Tuple{Vararg{Int}})`
  * `Derivative(order::Int...)`: equivalent to `Derivative(order)`

See also: [`differentiate`](@ref), [`differentiate!`](@ref), [`project(::Derivative, ::VectorSpace, ::VectorSpace)`](@ref) and [`project!(::LinearOperator, ::Derivative)`](@ref).

# Examples

```jldoctest
julia> Derivative(1)
Derivative{Int64}(1)

julia> Derivative(1, 2)
Derivative{Tuple{Int64, Int64}}((1, 2))
```
