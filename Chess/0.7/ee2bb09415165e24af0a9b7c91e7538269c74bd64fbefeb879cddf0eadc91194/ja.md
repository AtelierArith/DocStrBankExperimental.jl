```
variationtosan(g::SimpleGame, v::Vector{Move}; movenumbers=true)::String
variationtosan(g::Game, v::Vector{Move}; movenumbers=true)::String
```

変則を短い代数記法の文字列に変換します。

手のベクトル `v` は、ゲームの現在のボード位置からの合法的な手のシーケンスである必要があります。`movenumbers` が `true` の場合、手の番号が文字列に含まれます。

# 例

```julia-repl
julia> g = Game();

julia> domoves!(g, "d4", "Nf6", "c4", "e6", "Nf3");

julia> variationtosan(g, map(movefromstring, ["f8b4", "c1d2", "d8e7"]))
"3... Bb4+ 4. Bd2 Qe7"
```
