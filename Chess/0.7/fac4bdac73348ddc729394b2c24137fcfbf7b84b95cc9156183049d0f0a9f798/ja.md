```
isatbeginning(g::SimpleGame)::Bool
isatbeginning(g::Game)::Bool
```

ゲームの始まりにいる場合は `true` を返し、そうでない場合は `false` を返します。

ゲームの始まりにいるのは、まだゲームに手を加えていない場合か、始まりに戻った場合のいずれかです。

# 例

```julia-repl
julia> g = SimpleGame();

julia> isatbeginning(g)
true

julia> domove!(g, "e4");

julia> isatbeginning(g)
false

julia> back!(g);

julia> isatbeginning(g)
true
```
