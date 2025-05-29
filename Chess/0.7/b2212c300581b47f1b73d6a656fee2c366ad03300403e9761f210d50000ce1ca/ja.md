```
ply(g::SimpleGame)
ply(g::Game)
```

現在のノードのプレイ数。

ルートノードの場合は1、ルートノードの子の場合は2、などを返します。

# 例

```julia-repl
julia> g = Game();

julia> addmoves!(g, "d4", "Nf6", "c4", "g6", "Nc3", "Bg7");

julia> ply(g)
7

julia> back!(g);

julia> ply(g)
6

julia> tobeginning!(g);

julia> ply(g)
1
```
