```
Ell2{T<:Union{Weight,Tuple{Vararg{Weight}}}} <: BanachSpace
```

重み付き $\ell^2$ 空間。

フィールド：

  * `weight :: T`

コンストラクタ：

  * `Ell2(::Weight)`
  * `Ell2(::Tuple{Vararg{Weight}})`
  * `Ell2()`: `Ell2(IdentityWeight())` と同等
  * `Ell2(weight::Weight...)`: `Ell2(weight)` と同等

Unicode エイリアス [`ℓ²`](@ref) は、Julia REPL および多くのエディタで `\ell<tab>\^2<tab>` と入力することでタイプできます。

関連項目: [`Ell1`](@ref) と [`EllInf`](@ref)。

# 例

```jldoctest
julia> Ell2()
ℓ²()

julia> Ell2(BesselWeight(1.0))
ℓ²(BesselWeight(1.0))

julia> Ell2(BesselWeight(1.0), GeometricWeight(2.0))
ℓ²(BesselWeight(1.0), GeometricWeight(2.0))
```
