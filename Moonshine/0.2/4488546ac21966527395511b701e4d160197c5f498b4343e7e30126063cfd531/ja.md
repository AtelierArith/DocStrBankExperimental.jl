```julia
struct AncestralIntervals{T<:(AbstractVector{<:IntervalSets.AbstractInterval})} <: AbstractVector{IntervalSets.AbstractInterval}
```

区間のコレクション。

エッジ/頂点が祖先である区間の集合を表すことを目的としています。便利なショートハンド [`AIs`](@ref) を使用することをお勧めします。

[反復インターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration) と [配列インターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array) を実装しています。

[`AI`](@ref) および [`Ω`](@ref) も参照してください。

# フィールド

  * `data::AbstractVector{<:IntervalSets.AbstractInterval}`

# コンストラクタ

```julia
AncestralIntervals(data; simplify)
```

[`packages/Moonshine/7JVTP/src/AncestralIntervals.jl:78`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/AncestralIntervals.jl) で定義されています。

# 引数

`simplify = true` の場合、データに含まれる区間は簡略化されます: 詳細については [`simplify!`](@ref) を参照してください。

!!! warning
    多くのメソッドは `AIs` が簡略化されていることを前提としています。操作のシーケンスを最適化するために簡略化を無効にすることを検討するかもしれませんが、最終結果はおそらく簡略化すべきです。

