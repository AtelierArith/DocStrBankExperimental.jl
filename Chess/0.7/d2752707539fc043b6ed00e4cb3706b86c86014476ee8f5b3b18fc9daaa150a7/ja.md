```
continuations(n::GameNode)::Vector{Move}
continuations(g::Game)::Vector{Move}
```

ゲームツリーのこのノードでのすべての手。

現在のノードの各子ノードに対して1つの手。最初の要素はメインラインです。

# 例

```julia-repl
julia> g = Game();

julia> addmoves!(g, "e4", "e5");

julia> back!(g);

julia> addmove!(g, "c5");

julia> back!(g);

julia> continuations(g)
2-element Array{Move,1}:
 Move(e7e5)
 Move(c7c5)
```
