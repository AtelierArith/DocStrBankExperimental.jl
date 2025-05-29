```
CartesianProduct{T<:Tuple{Vararg{VectorSpace}}} <: CartesianSpace
```

いくつかの [`VectorSpace`](@ref) の直積から得られる直交空間。

フィールド:

  * `spaces :: T`

コンストラクタ:

  * `CartesianProduct(::Tuple{Vararg{VectorSpace}})`
  * `CartesianProduct(spaces::VectorSpace...)`: `CartesianProduct(spaces)` と同等
  * `×(s₁::VectorSpace, s₂::VectorSpace)`: `CartesianProduct((s₁, s₂))` と同等
  * `×(s₁::CartesianProduct, s₂::CartesianProduct)`: `CartesianProduct((s₁.spaces..., s₂.spaces...))` と同等
  * `×(s₁::CartesianProduct, s₂::VectorSpace)`: `CartesianProduct((s₁.spaces..., s₂))` と同等
  * `×(s₁::VectorSpace, s₂::CartesianProduct)`: `CartesianProduct((s₁, s₂.spaces...))` と同等

関連項目: [`×`](@ref), [`CartesianPower`](@ref), [`^(::VectorSpace, ::Int)`](@ref).

# 例

```jldoctest
julia> s = CartesianProduct(Taylor(1), Fourier(2, 1.0), Chebyshev(3))
Taylor(1) × Fourier(2, 1.0) × Chebyshev(3)

julia> spaces(s)
(Taylor(1), Fourier(2, 1.0), Chebyshev(3))

julia> nspaces(s)
3
```
