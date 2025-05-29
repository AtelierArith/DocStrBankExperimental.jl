```
⊗(s₁::BaseSpace, s₂::BaseSpace)
⊗(s₁::TensorSpace, s₂::TensorSpace)
⊗(s₁::TensorSpace, s₂::BaseSpace)
⊗(s₁::BaseSpace, s₂::TensorSpace)
```

いくつかの [`SequenceSpace`](@ref) のテンソル積から [`TensorSpace`](@ref) を作成します。

参照: [`TensorSpace`](@ref)。

# 例

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
