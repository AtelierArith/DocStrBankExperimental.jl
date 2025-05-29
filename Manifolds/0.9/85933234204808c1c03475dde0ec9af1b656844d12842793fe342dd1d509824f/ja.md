```
convert(::Type{PoincareHalfSpaceTVector}, p::HyperboloidPoint, ::HyperboloidTVector)
convert(::Type{PoincareHalfSpaceTVector}, p::P, X::T) where {P<:AbstractVector, T<:AbstractVector}
```

`p`における[`HyperboloidTVector`](@ref) `X`を、[`Hyperbolic`](@ref)多様体$\mathcal H^n$上の[`PoincareHalfSpaceTVector`](@ref)に変換するには、ハイパーボロイドからポアンカレ半空間への等距変換$π$のプッシュフォワード$π_*(p)[X]$を計算します。これは[`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref)を参照してください。

これは、そこにあるアプローチと同様に、ポアンカレボールモデルを中間ステップとして使用することによって行われます。 ```
