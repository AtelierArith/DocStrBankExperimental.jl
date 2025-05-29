```
variationtosan(board::Board, v::Vector{Move};
               startply=1, movenumbers=true)::String
```

変則を短い代数記法の文字列に変換します。

移動のベクトル `v` は、ボードの位置からの合法的な移動のシーケンスである必要があります。`movenumbers` が `true` の場合、移動番号が文字列に含まれます。移動は1から番号付けされますが、`startply` パラメータを通じて他の変数が供給されると、異なる番号付けが行われます。

# 例

```julia-repl
julia> b = startboard();

julia> variationtosan(b, map(movefromstring, ["e2e4", "e7e5", "g1f3", "b8c6"]))
"1. e4 e5 2. Nf3 Nc6"
```
