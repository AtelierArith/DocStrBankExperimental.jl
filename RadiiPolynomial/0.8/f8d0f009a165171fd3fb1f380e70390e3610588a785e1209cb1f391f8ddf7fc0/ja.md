```
EllInf{T<:Union{Weight,Tuple{Vararg{Weight}}}} <: BanachSpace
```

重み付き $\ell^\infty$ 空間。

フィールド:

  * `weight :: T`

コンストラクタ:

  * `EllInf(::Weight)`
  * `EllInf(::Tuple{Vararg{Weight}})`
  * `EllInf()`: `EllInf(IdentityWeight())` と同等
  * `EllInf(weight::Weight...)`: `EllInf(weight)` と同等

Unicode エイリアス [`ℓ∞`](@ref) は、Julia REPL や多くのエディタで `\ell<tab>\infty<tab>` と入力することでタイプできます。

関連項目: [`Ell1`](@ref) と [`Ell2`](@ref)。

# 例

```jldoctest
julia> EllInf()
ℓ∞()

julia> EllInf(GeometricWeight(1.0))
ℓ∞(GeometricWeight(1.0))

julia> EllInf(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ∞(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
