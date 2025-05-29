```
setdateplayed!(g::SimpleGame, date::Date)
setdateplayed!(g::Game, date::Date)
```

指定された日付を使用して「Date」ヘッダーを設定します。標準PGN日付形式を使用します。

# 例

```julia-repl
julia> using Dates

julia> g = Game();

julia> setdateplayed!(g, Date(2020, 10, 08));

julia> headervalue(g, "Date")
"2020.10.08"

julia> dateplayed(g)
2020-10-08
```
