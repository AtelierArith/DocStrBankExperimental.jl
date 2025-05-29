```julia
struct Tree <: Moonshine.AbstractGenealogy
```

コアレセントツリー。

関連情報として[`Arg`](@ref)を参照してください。

# フィールド

  * `graph::Graphs.SimpleGraphs.SimpleDiGraph{Int32}`: ツリーのトポロジー
  * `latitudes::Vector{Float64}`: 頂点の緯度
  * `sequences::Vector{Moonshine.Sequence}`: 頂点のハプロタイプ
  * `sample::Moonshine.Sample`: 関連する[`Sample`](@ref)
  * `logdensity::Base.RefValue{DoubleFloats.Double64}`: 関連するpdfの対数値

# コンストラクタ

!!! info
    ランダムコンストラクタは[`Sample`](@ref)のランダムコンストラクタを呼び出します。


!!! warning
    これらは実際にはツリーを構築しません。そのためには、[`build!(rng, tree)`](@ref)を参照してください。


```julia
Tree(graph, latitudes, sequences, sample, logdensity)
Tree(graph, latitudes, sequences, sample, logdensity)
```

[`packages/Moonshine/7JVTP/src/Tree.jl:42`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Tree.jl)で定義されています。

```julia
Tree(sample)
```

[`packages/Moonshine/7JVTP/src/Tree.jl:54`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Tree.jl)で定義されています。

```julia
Tree(rng, n, μ, ρ, Ne, sequence_length)
```

[`packages/Moonshine/7JVTP/src/Tree.jl:66`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Tree.jl)で定義されています。

# 引数

引数は[`Sample`](@ref)と同じです。
