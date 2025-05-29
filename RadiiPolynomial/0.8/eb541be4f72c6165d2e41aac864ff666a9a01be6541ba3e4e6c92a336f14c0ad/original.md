```
CartesianPower{T<:VectorSpace} <: CartesianSpace
```

Cartesian space resulting from the cartesian product of the same [`VectorSpace`](@ref).

Fields:

  * `space :: T`
  * `n :: Int`

Constructors:

  * `CartesianPower(::VectorSpace, ::Int)`
  * `^(::VectorSpace, ::Int)`: equivalent to `CartesianPower(::VectorSpace, ::Int)`

See also: [`^(::VectorSpace, ::Int)`](@ref), [`CartesianProduct`](@ref) and [`×`](@ref).

# Examples

```jldoctest
julia> s = CartesianPower(Taylor(1), 3)
Taylor(1)³

julia> space(s)
Taylor(1)

julia> nspaces(s)
3
```
