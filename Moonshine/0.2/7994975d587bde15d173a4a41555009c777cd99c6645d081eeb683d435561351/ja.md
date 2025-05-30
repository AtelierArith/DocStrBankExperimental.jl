```julia
struct Arg <: Moonshine.AbstractGenealogy
```

祖先再結合グラフ。

関連情報として、[`Tree`](@ref)を参照してください。

# フィールド

  * `graph::Graphs.SimpleGraphs.SimpleDiGraph{Int32}`: グラフのトポロジー
  * `latitudes::Vector{Float64}`: 頂点の緯度
  * `recombination_mask::Vector{Moonshine.AncestralIntervals{Vector{IntervalSets.Interval{:closed, :open, Float64}}}}`: 祖先区間の∩-マスク
  * `mrca::Base.RefValue{Int32}`: Argの祖先の最も最近共通祖先
  * `sequences::Vector{Moonshine.Sequence}`: 頂点のハプロタイプ
  * `ancestral_intervals::Dict{Graphs.SimpleGraphs.SimpleEdge{Int32}, Moonshine.AncestralIntervals{Vector{IntervalSets.Interval{:closed, :open, Float64}}}}`: 辺の祖先区間
  * `sample::Moonshine.Sample`: 関連する[`Sample`](@ref)
  * `logdensity::Base.RefValue{DoubleFloats.Double64}`: 関連するpdfの対数値

# コンストラクタ

!!! info
    ランダムコンストラクタは[`Sample`](@ref)のランダムコンストラクタを呼び出します。


!!! warning
    これらは実際にはargを構築しません。そのためには、[`build!(rng, arg)`](@ref)を参照してください。


```julia
Arg(
    graph,
    latitudes,
    recombination_mask,
    mrca,
    sequences,
    ancestral_intervals,
    sample,
    logdensity
)
Arg(
    graph,
    latitudes,
    recombination_mask,
    mrca,
    sequences,
    ancestral_intervals,
    sample,
    logdensity
)
```

[`packages/Moonshine/7JVTP/src/Arg/Arg.jl:43`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl)で定義されています。

```julia
Arg(tree)
```

[`packages/Moonshine/7JVTP/src/Arg/Arg.jl:61`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl)で定義されています。

```julia
Arg(rng, n, μ, ρ, Ne, sequence_length)
```

[`packages/Moonshine/7JVTP/src/Arg/Arg.jl:77`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl)で定義されています。

# 引数

  * `tree`: 共通祖先の[`Tree`](@ref)
  * その他の引数は[`Sample`](@ref)と同じです。
