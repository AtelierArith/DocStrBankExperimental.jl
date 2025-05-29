```
TensorSpace{T<:Tuple{Vararg{BaseSpace}}} <: SequenceSpace
```

いくつかの [`BaseSpace`](@ref) のテンソル積から得られるテンソル空間。

フィールド:

  * `spaces :: T`

コンストラクタ:

  * `TensorSpace(::Tuple{Vararg{BaseSpace}})`
  * `TensorSpace(spaces::BaseSpace...)`: `TensorSpace(spaces)` と同等
  * `⊗(s₁::BaseSpace, s₂::BaseSpace)`: `TensorSpace((s₁, s₂))` と同等
  * `⊗(s₁::TensorSpace, s₂::TensorSpace)`: `TensorSpace((s₁.spaces..., s₂.spaces...))` と同等
  * `⊗(s₁::TensorSpace, s₂::BaseSpace)`: `TensorSpace((s₁.spaces..., s₂))` と同等
  * `⊗(s₁::BaseSpace, s₂::TensorSpace)`: `TensorSpace((s₁, s₂.spaces...))` と同等

詳細は: [`⊗`](@ref) を参照。

# 例

```jldoctest
julia> s = TensorSpace(Taylor(1), Fourier(2, 1.0), Chebyshev(3))
Taylor(1) ⊗ Fourier(2, 1.0) ⊗ Chebyshev(3)

julia> spaces(s)
(Taylor(1), Fourier(2, 1.0), Chebyshev(3))
```
