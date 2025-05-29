```
nflverse_game_id(season::Number,week::Number,away::AbstractString,home::AbstractString)
```

nflverseゲームIDを確認して計算します。

# 例

```julia-repl
julia> nflverse_game_id(2022, 2, "LAC", "KC")
"2022_02_LAC_KC"
```
