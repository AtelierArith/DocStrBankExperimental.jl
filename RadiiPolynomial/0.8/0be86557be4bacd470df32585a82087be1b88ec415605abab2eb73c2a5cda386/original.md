```
⊗(s₁::BaseSpace, s₂::BaseSpace)
⊗(s₁::TensorSpace, s₂::TensorSpace)
⊗(s₁::TensorSpace, s₂::BaseSpace)
⊗(s₁::BaseSpace, s₂::TensorSpace)
```

Create a [`TensorSpace`](@ref) from the tensor product of some [`SequenceSpace`](@ref).

See also: [`TensorSpace`](@ref).

# Examples

```jldoctest
julia> Taylor(1) ⊗ Fourier(2, 1.0)
Taylor(1) ⊗ Fourier(2, 1.0)

julia> Taylor(1) ⊗ Fourier(2, 1.0) ⊗ Chebyshev(3)
Taylor(1) ⊗ Fourier(2, 1.0) ⊗ Chebyshev(3)

julia> Taylor(1) ⊗ (Fourier(2, 1.0) ⊗ Chebyshev(3))
Taylor(1) ⊗ Fourier(2, 1.0) ⊗ Chebyshev(3)

julia> (Taylor(1) ⊗ Fourier(2, 1.0)) ⊗ Chebyshev(3)
Taylor(1) ⊗ Fourier(2, 1.0) ⊗ Chebyshev(3)
```
