```
Evaluation{T<:Union{Nothing,Number,Tuple{Vararg{Union{Nothing,Number}}}}} <: SpecialOperator
```

Generic evaluation operator. A value of `nothing` indicates that no evaluation should be performed.

Field:

  * `value :: T`

Constructors:

  * `Evaluation(::Union{Nothing,Number})`
  * `Evaluation(::Tuple{Vararg{Union{Nothing,Number}}})`
  * `Evaluation(value::Union{Number,Nothing}...)`: equivalent to `Evaluation(value)`

See also: [`evaluate`](@ref), [`evaluate!`](@ref), [`project(::Evaluation, ::VectorSpace, ::VectorSpace)`](@ref) and [`project!(::LinearOperator, ::Evaluation)`](@ref).

# Examples

```jldoctest
julia> Evaluation(1.0)
Evaluation{Float64}(1.0)

julia> Evaluation(1.0, nothing, 2.0)
Evaluation{Tuple{Float64, Nothing, Float64}}((1.0, nothing, 2.0))
```
