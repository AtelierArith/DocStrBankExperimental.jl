`KRatios`は、KRatio型のハイパースペクトル同等物を表します。`KRatios`オブジェクト内の各ピクセルは、同じ未知の標準特性、同じX線ライン、およびその他の特性によって特徴付けられなければなりません。

メソッド:

```
> Base.getindex(krs::KRatios, idx::Int...)
> Base.getindex(krs::KRatios, ci::CartesianIndex)
> Base.size(krs::KRatios, [idx::Int])
> Base.CartesianIndices(krs::KRatios)
> normalizek(krs::AbstractVector{<:KRatios}; norm::Float32=1.0f)::Vector{KRatios}
> normalizek(krs::AbstractVector{KRatio}; norm::Float32=1.0f)::Vector{KRatio}
> brightest(krs::Union{KRatios, KRatio})
> colorize(krs::AbstractVector{<:KRatios}, red::Element, green::Element, blue::Element, normalize=:All[|:Each])
> colorize(krs::AbstractVector{<:KRatios}, elms::AbstractVector{Element}, normalize=:All)
> Base.getindex(krs::AbstractVector{<:KRatios}, elm::Element) # グレースケール画像
> Base.getindex(krs::AbstractVector{<:KRatios}, red::Element, green::Element)  # 赤-緑画像
> Base.getindex(krs::AbstractVector{<:KRatios}, red::Element, green::Element, blue::Element) # RGB画像
```
