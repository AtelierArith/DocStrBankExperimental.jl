```
sym_analyse_coordstate(
    d,
    coordState::CoordState,
    symmetries::Array{Permutation},
    anaSpec::AnalysisSpecification,
    stdBasis::StandardBasis=missing,
    kernelPolytope::Union{HPolytope{Float64,Array{Float64,1}},VPolytope{Float64,Array{Float64,1}},Missing}=missing,
    bipartiteWeylBasis::Union{Vector{Array{Complex{Float64},2}},Missing}=missing,
    dictionaries::Union{Any,Missing}=missing,
    mubSet::Union{Vector{Vector{Vector{ComplexF64}}},Missing}=missing,
    boundedCoordEWs::Union{Array{BoundedCoordEW},Missing}=missing,
    precision=10,
    relUncertainity=0.0
)
```

`d`次元の`coordState`に対して、与えられた`anaSpec`および対応する分析オブジェクトと対称性分析に基づいて`AnalysedCoordState`を返します。

エンタングルメントチェックを実行しない場合や、変数として分析オブジェクトが渡されていない場合、`anaSpec`の対応するプロパティは`false`である必要があります。この場合、`AnalysedCoordState`の対応するプロパティは`missing`として返されます。
