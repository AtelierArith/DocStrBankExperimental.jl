```
Scale{T<:Union{Number,Tuple{Vararg{Number}}}} <: SpecialOperator
```

Generic scale operator.

Field:

  * `value :: T`

Constructors:

  * `Scale(::Number)`
  * `Scale(::Tuple{Vararg{Number}})`
  * `Scale(value::Number...)`: equivalent to `Scale(value)`

See also: [`scale`](@ref), [`scale!`](@ref), [`project(::Scale, ::VectorSpace, ::VectorSpace)`](@ref) and [`project!(::LinearOperator, ::Scale)`](@ref).

# Examples

```jldoctest
julia> Scale(1.0)
Scale{Float64}(1.0)

julia> Scale(1.0, 2.0)
Scale{Tuple{Float64, Float64}}((1.0, 2.0))
```
