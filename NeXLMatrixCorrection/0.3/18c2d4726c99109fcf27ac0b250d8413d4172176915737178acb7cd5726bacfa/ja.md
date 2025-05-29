```
quantify(
    name::Union{String, Label},
    measured::Vector{KRatio}, 
    iteration::Iteration = Iteration(mc=XPP, fc=ReedFluorescence, cc=Coating);
    maxIter::Int = 100, 
    estComp::Union{Nothing,Material}=nothing, 
    coating::Union{Nothing, Pair{CharXRay, <:Material}}=nothing
)::IterationResult

quantify(
    measured::AbstractVector{KRatios{T}},
    iteration::Iteration = Iteration(mc=XPP, fc=NullFluorescence, cc=NullCoating);
    kro::KRatioOptimizer = SimpleKRatioOptimizer(1.5),
    maxIter::Int = 100, 
    estComp::Union{Nothing,Material}=nothing, 
    coating::Union{Nothing, Pair{CharXRay, Material}}=nothing
)

`iter`で説明されている反復手続きを実行し、`measured` k-比を使用して`IterationResult`オブジェクト内の最良の推定`Material`を生成します。 第三の形式は、フィルターフィットスペクトルからk-比を定量化するのを容易にします。 `estComp`は、組成の最初の推定値としてオプションです。 これは、多くの類似したk-比を定量化する際に便利な最適化となる場合があります（例えば、ハイパースペクトル上の点など）。

`coating`は、ペアになった`Material`のコーティング層の厚さを推定するために使用される、サンプルに存在しないCharXRayを定義します。
```
