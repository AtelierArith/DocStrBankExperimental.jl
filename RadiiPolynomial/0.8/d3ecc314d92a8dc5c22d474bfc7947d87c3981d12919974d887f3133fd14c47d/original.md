```
Integral{T<:Union{Int,Tuple{Vararg{Int}}}} <: SpecialOperator
```

Generic integral operator.

Field:

  * `order :: T`

Constructors:

  * `Integral(::Int)`
  * `Integral(::Tuple{Vararg{Int}})`
  * `Integral(order::Int...)`: equivalent to `Integral(order)`

See also: [`integrate`](@ref), [`integrate!`](@ref), [`project(::Integral, ::VectorSpace, ::VectorSpace)`](@ref) and [`project!(::LinearOperator, ::Integral)`](@ref).

# Examples

```jldoctest
julia> Integral(1)
Integral{Int64}(1)

julia> Integral(1, 2)
Integral{Tuple{Int64, Int64}}((1, 2))
```
