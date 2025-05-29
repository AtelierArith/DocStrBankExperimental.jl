```
function randframe(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Int64,
    nedges::Int64,
    facts::Vector{SyntaxLeaf}
end
```

ランダムなクリプケフレームを返します。これは、[`SoleLogics.ExplicitCrispUniModalFrame`](@ref)として解釈される有向グラフです。基盤となるグラフは、[`Graphs.SimpleGraphs.SimpleDiGraph`](@ref)を使用して生成されます。

# 引数:

  * `rng` は乱数生成器、またはそれを作成するために使用されるシードです；
  * `nworld` はフレーム内の世界（ノード）の数です。世界は `1` から `nworld` までの番号が付けられます。
  * `nedges` はフレーム内の関係（エッジ）の数です；
  * `facts` は一般的な[`SyntaxLeaf`](@ref)のベクターです。

他にも[`SyntaxLeaf`](@ref)、[`Graphs.SimpleGraphs.SimpleDiGraph`](@ref)、[`SoleLogics.ExplicitCrispUniModalFrame`](@ref)を参照してください。
