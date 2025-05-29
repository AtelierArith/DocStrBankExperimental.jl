```
Shift{T<:Union{Number,Tuple{Vararg{Number}}}} <: SpecialOperator
```

Generic shift operator.

Field:

  * `value :: T`

Constructors:

  * `Shift(::Number)`
  * `Shift(::Tuple{Vararg{Number}})`
  * `Shift(value::Number...)`: equivalent to `Shift(value)`

See also: [`shift`](@ref), [`shift!`](@ref), [`project(::Shift, ::VectorSpace, ::VectorSpace)`](@ref) and [`project!(::LinearOperator, ::Shift)`](@ref).

# Examples

```jldoctest
julia> Shift(1.0)
Shift{Float64}(1.0)

julia> Shift(1.0, 2.0)
Shift{Tuple{Float64, Float64}}((1.0, 2.0))
```
