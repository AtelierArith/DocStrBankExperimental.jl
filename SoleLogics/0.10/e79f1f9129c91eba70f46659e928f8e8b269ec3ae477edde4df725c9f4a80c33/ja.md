```
function randmodel(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG,]
    nworlds::Integer,
    nedges::Integer,
    facts::Vector{SyntaxLeaf};
    truthvalues::Union{AbstractAlgebra,AbstractVector{<:Truth}}
)
```

# 引数

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: 擬似乱数生成器;
  * `nworlds::Int64`: フレーム内の世界（ノード）の数（`1` から `nworld` までの番号が付けられます）。
  * `nedges::Int64`: フレーム内の関係（エッジ）の数;
  * `facts::Int64`: 特定の評価関数が [`Truth`](@ref) 値を関連付けることができる事実を表す一般的な [`SyntaxLeaf`](@ref) のベクター;
  * `truthvalues::Union{AbstractAlgebra,AbstractVector{<:Truth}}`: `facts` の各要素に関連付けられる [`Truth`](@ref) 値。

# 例

```julia-repl
julia> randmodel(Random.MersenneTwister(42),5,10, [Atom("s"), Atom("p")], BooleanAlgebra())
KripkeStructure{SoleLogics.ExplicitCrispUniModalFrame{SoleLogics.World{Int64}, Graphs.SimpleGraphs.SimpleDiGraph{Int64}}, Dict{SoleLogics.World{Int64}, TruthDict{Dict{Atom{String}, BooleanTruth}}}} with
- frame = SoleLogics.ExplicitCrispUniModalFrame{SoleLogics.World{Int64}, Graphs.SimpleGraphs.SimpleDiGraph{Int64}} with
- worlds = ["1", "2", "3", "4", "5"]
- accessibles =
        1 -> [2, 3, 5]
        2 -> [1, 4, 5]
        3 -> []
        4 -> [1, 2]
        5 -> [1, 2]
- valuations =
        1 -> TruthDict([s => ⊥, p => ⊤])
        2 -> TruthDict([s => ⊥, p => ⊥])
        3 -> TruthDict([s => ⊥, p => ⊥])
        4 -> TruthDict([s => ⊤, p => ⊤])
        5 -> TruthDict([s => ⊤, p => ⊤])
```

See also [`AbstractAlgebra`](@ref), [`SyntaxLeaf`](@ref), [`Truth`](@ref).
