```
function randframe(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Integer,
    nedges::Integer,
end
```

ランダムなクリプケフレームを返します。これは、[`SoleLogics.ExplicitCrispUniModalFrame`](@ref)として解釈される有向グラフです。基盤となるグラフは、[`Graphs.SimpleGraphs.SimpleDiGraph`](@ref)を使用して生成されます。

# 引数

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: ランダム数生成器;
  * `nworlds::Int64`: フレーム内の世界（ノード）の数（`1`から`nworld`までの番号が付けられます）。
  * `nedges::Int64`: フレーム内の関係（エッジ）の数;

# 例

```julia-repl
julia> randframe(Random.MersenneTwister(42),5,10)
SoleLogics.ExplicitCrispUniModalFrame{SoleLogics.World{Int64}, Graphs.SimpleGraphs.SimpleDiGraph{Int64}} with
- worlds = ["1", "2", "3", "4", "5"]
- accessibles =
        1 -> [2, 3, 5]
        2 -> [1, 4, 5]
        3 -> []
        4 -> [1, 2]
        5 -> [1, 2]
```

さらに[`SoleLogics.ExplicitCrispUniModalFrame`](@ref)、[`SyntaxLeaf`](@ref)、[`Graphs.SimpleGraphs.SimpleDiGraph`](@ref)を参照してください。
