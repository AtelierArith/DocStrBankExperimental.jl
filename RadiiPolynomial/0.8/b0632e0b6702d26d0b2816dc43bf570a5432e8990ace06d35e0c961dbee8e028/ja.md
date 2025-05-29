```
Ell1{T<:Union{Weight,Tuple{Vararg{Weight}}}} <: BanachSpace
```

重み付き $\ell^1$ 空間。

フィールド:

  * `weight :: T`

コンストラクタ:

  * `Ell1(::Weight)`
  * `Ell1(::Tuple{Vararg{Weight}})`
  * `Ell1()`: `Ell1(IdentityWeight())` と同等
  * `Ell1(weight::Weight...)`: `Ell1(weight)` と同等

Unicode エイリアス [`ℓ¹`](@ref) は、Julia REPL および多くのエディタで `\ell<tab>\^1<tab>` と入力することでタイプできます。

関連項目: [`Ell2`](@ref) と [`EllInf`](@ref)。

# 例

```jldoctest
julia> Ell1()
ℓ¹()

julia> Ell1(GeometricWeight(1.0))
ℓ¹(GeometricWeight(1.0))

julia> Ell1(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ¹(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
