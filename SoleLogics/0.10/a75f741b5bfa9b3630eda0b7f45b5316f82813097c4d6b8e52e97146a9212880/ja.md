```
function check(
    φ::SyntaxTree,
    i::AbstractKripkeStructure,
    w::Union{Nothing,AnyWorld,<:AbstractWorld} = nothing;
    use_memo::Union{Nothing,AbstractDict{<:Formula,<:Vector{<:AbstractWorld}}} = nothing,
    perform_normalization::Bool = true,
    memo_max_height::Union{Nothing,Int} = nothing,
)::Bool
```

特定の世界における式をチェックします [`KripkeStructure`](@ref)。

# 例

```julia-repl
julia> using Graphs, Random

julia> @atoms String p q
2-element Vector{Atom{String}}:
 Atom{String}("p")
 Atom{String}("q")

julia> fmodal = randformula(Random.MersenneTwister(14), 3, [p,q], SoleLogics.BASE_MODAL_CONNECTIVES)
¬□(p ∨ q)

# 特別なグラフ、呼ばれるクリプケフレームが作成されます。
# ノードは世界と呼ばれ、エッジは世界間の関係です。
julia> worlds = SoleLogics.World.(1:5) # 5つの世界が作成され、1から5まで番号が付けられます

julia> edges = Edge.([(1,2), (1,3), (2,4), (3,4), (3,5)])

julia> kframe = SoleLogics.ExplicitCrispUniModalFrame(worlds, Graphs.SimpleDiGraph(edges))

# 評価関数は各世界でどの事実が真であるかを確立します
julia> valuation = Dict([
    worlds[1] => TruthDict([p => true, q => false]),
    worlds[2] => TruthDict([p => true, q => true]),
    worlds[3] => TruthDict([p => true, q => false]),
    worlds[4] => TruthDict([p => false, q => false]),
    worlds[5] => TruthDict([p => false, q => true]),
 ])

# クリプケフレームと評価関数がクリプケ構造に統合されます
julia> kstruct = KripkeStructure(kframe, valuation)

julia> [w => check(fmodal, kstruct, w) for w in worlds]
5-element Vector{Pair{SoleLogics.World{Int64}, Bool}}:
 SoleLogics.World{Int64}(1) => 0
 SoleLogics.World{Int64}(2) => 1
 SoleLogics.World{Int64}(3) => 1
 SoleLogics.World{Int64}(4) => 0
 SoleLogics.World{Int64}(5) => 0
```

さらに [`SyntaxTree`](@ref)、[`AbstractWorld`](@ref)、[`KripkeStructure`](@ref) を参照してください。
