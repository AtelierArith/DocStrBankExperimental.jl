```
CartesianProduct{T<:Tuple{Vararg{VectorSpace}}} <: CartesianSpace
```

Cartesian space resulting from the cartesian product of some [`VectorSpace`](@ref).

Field:

  * `spaces :: T`

Constructors:

  * `CartesianProduct(::Tuple{Vararg{VectorSpace}})`
  * `CartesianProduct(spaces::VectorSpace...)`: equivalent to `CartesianProduct(spaces)`
  * `×(s₁::VectorSpace, s₂::VectorSpace)`: equivalent to `CartesianProduct((s₁, s₂))`
  * `×(s₁::CartesianProduct, s₂::CartesianProduct)`: equivalent to `CartesianProduct((s₁.spaces..., s₂.spaces...))`
  * `×(s₁::CartesianProduct, s₂::VectorSpace)`: equivalent to `CartesianProduct((s₁.spaces..., s₂))`
  * `×(s₁::VectorSpace, s₂::CartesianProduct)`: equivalent to `CartesianProduct((s₁, s₂.spaces...))`

See also: [`×`](@ref), [`CartesianPower`](@ref), [`^(::VectorSpace, ::Int)`](@ref).

# Examples

```jldoctest
julia> s = CartesianProduct(Taylor(1), Fourier(2, 1.0), Chebyshev(3))
Taylor(1) × Fourier(2, 1.0) × Chebyshev(3)

julia> spaces(s)
(Taylor(1), Fourier(2, 1.0), Chebyshev(3))

julia> nspaces(s)
3
```
