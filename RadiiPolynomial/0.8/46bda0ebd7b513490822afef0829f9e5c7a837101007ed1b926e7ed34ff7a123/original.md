```
TensorSpace{T<:Tuple{Vararg{BaseSpace}}} <: SequenceSpace
```

Tensor space resulting from the tensor product of some [`BaseSpace`](@ref).

Field:

  * `spaces :: T`

Constructors:

  * `TensorSpace(::Tuple{Vararg{BaseSpace}})`
  * `TensorSpace(spaces::BaseSpace...)`: equivalent to `TensorSpace(spaces)`
  * `⊗(s₁::BaseSpace, s₂::BaseSpace)`: equivalent to `TensorSpace((s₁, s₂))`
  * `⊗(s₁::TensorSpace, s₂::TensorSpace)`: equivalent to `TensorSpace((s₁.spaces..., s₂.spaces...))`
  * `⊗(s₁::TensorSpace, s₂::BaseSpace)`: equivalent to `TensorSpace((s₁.spaces..., s₂))`
  * `⊗(s₁::BaseSpace, s₂::TensorSpace)`: equivalent to `TensorSpace((s₁, s₂.spaces...))`

See also: [`⊗`](@ref).

# Examples

```jldoctest
julia> s = TensorSpace(Taylor(1), Fourier(2, 1.0), Chebyshev(3))
Taylor(1) ⊗ Fourier(2, 1.0) ⊗ Chebyshev(3)

julia> spaces(s)
(Taylor(1), Fourier(2, 1.0), Chebyshev(3))
```
