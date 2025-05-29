```
BagCount{T <: AbstractAggregation}
```

呼び出されると、内部に格納された[`AbstractAggregation`](@ref)を適用し、$x ↦ \log(x + 1)$変換の結果にバグサイズを含むもう1つの要素を追加するラッパー型です。

ファンクタとして使用されます：

```
(bc::BagCount)(x, bags[, w])
```

ここで、`x`は`AbstractMatrix`または`missing`のいずれかで、`bags`は[`AbstractBags`](@ref)構造体であり、オプションで`w`は重みの`AbstractVector`です。

# 例

```jldoctest
julia> x = Float32[0 1 2; 3 4 5]
2×3 Matrix{Float32}:
 0.0  1.0  2.0
 3.0  4.0  5.0

julia> b = bags([1:1, 2:3])
AlignedBags{Int64}(UnitRange{Int64}[1:1, 2:3])

julia> a = vcat(SegmentedMean(2), SegmentedMax(2))
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0])

julia> a(x, b)
4×2 Matrix{Float32}:
 0.0  1.5
 3.0  4.5
 0.0  2.0
 3.0  5.0

julia> BagCount(a)(x, b)
5×2 Matrix{Float32}:
 0.0       1.5
 3.0       4.5
 0.0       2.0
 3.0       5.0
 0.693147  1.09861
```

参照：[`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
