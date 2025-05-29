```
AggregationStack{T <: Tuple{Vararg{AbstractAggregation}}} <: AbstractAggregation
```

1つ以上の`AbstractAggregation`の連結を実装するコンテナです。

例えば、単一のオペレーターには`AggregationStack(SegmentedMean([t::Type, ]d))`を、連結には`SegmentedPNormLSE([t::Type, ]d)`を使用して構築します。これらの呼び出しでは、オペレーター内のすべてのパラメーターが、型`t`がさらに指定されない限り、ランダムに`Float32`配列として初期化されます。もう1つのオプションは、2つのオペレーターを`vcat`で結合することです。

ネストされたスタックは、構築時に単一レベルの構造にフラット化されます。例を参照してください。

ファンクターとして使用することを意図しています：

```
(a::AggregationStack)(x, bags[, w])
```

ここで、`x`は`AbstractMatrix`または`missing`、`bags`は[`AbstractBags`](@ref)構造体であり、オプションで`w`は重みの`AbstractVector`です。

# 例

```jldoctest
julia> a = AggregationStack(SegmentedMean(2), SegmentedMax(2))
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0])

julia> a(Float32[0 1 2; 3 4 5], bags([1:1, 2:3]))
4×2 Matrix{Float32}:
 0.0  1.5
 3.0  4.5
 0.0  2.0
 3.0  5.0

julia> a = AggregationStack(SegmentedMean(2), AggregationStack(SegmentedMax(2)))
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0])

julia> a = SegmentedMeanMax(Float32, 2)
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0])

julia> vcat(SegmentedMean(2), SegmentedMax(2))
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0])

```

参照：[`AbstractAggregation`](@ref)、[`SegmentedSum`](@ref)、[`SegmentedMax`](@ref)、     [`SegmentedMean`](@ref)、[`SegmentedPNorm`](@ref)、[`SegmentedLSE`](@ref)。
