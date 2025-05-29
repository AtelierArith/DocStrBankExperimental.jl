```
convert(::Type{PoincareHalfSpaceTangentVector}, p::HyperboloidPoint, ::HyperboloidTangentVector)
convert(::Type{PoincareHalfSpaceTangentVector}, p::P, X::T) where {P<:AbstractVector, T<:AbstractVector}
```

`p`における[`HyperboloidTangentVector`](@ref) `X`を[`PoincareHalfSpaceTangentVector`](@ref)に変換するには、ハイパーボロイドからポアンカレ半空間への同型写像$π$のプッシュフォワード$π_*(p)[X]$を計算します。これは[`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref)を参照してください。

これは、そこにあるアプローチと同様に、すなわちポアンカレボールモデルを中間ステップとして使用することによって行われます。 ```
