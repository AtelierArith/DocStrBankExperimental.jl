```
isatend(g::SimpleGame)::Bool
isatend(g::Game)::Bool
```

ゲームの終わりにいる場合は `true` を返し、そうでない場合は `false` を返します。

# 例

```julia-repl
julia> g = SimpleGame();

julia> isatend(g)
true

julia> domove!(g, "Nf3");

julia> isatend(g)
true

julia> back!(g);

julia> isatend(g)
false
```
