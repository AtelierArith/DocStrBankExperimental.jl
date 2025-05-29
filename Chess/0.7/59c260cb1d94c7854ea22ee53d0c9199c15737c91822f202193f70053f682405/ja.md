```
dateplayed(g::SimpleGame)::Union{Date, Nothing}
dateplayed(g::Game)::Union{Date, Nothing}
```

ゲームがプレイされた日付、または `nothing`。

この関数はPGNの日付タグを利用し、日付が不完全または不正確にフォーマットされている場合でも、妥当なデフォルトで堅牢に動作するように試みます。ISO形式のYYYY-MM-DD日付とPGN形式のYYYY.MM.DD日付の両方を処理します。月または日が欠けている場合、それらは1に置き換えられます。失敗した場合は、`nothing`を返します。

# 例

```julia-repl
julia> g = Game();

julia> setheadervalue!(g, "Date", "2019.09.20");

julia> dateplayed(g)
2019-09-20

julia> setheadervalue!(g, "Date", "2019.09.??");

julia> dateplayed(g)
2019-09-01

julia> setheadervalue!(g, "Date", "2019.??.??");

julia> dateplayed(g)
2019-01-01

julia> setheadervalue!(g, "Date", "*");

julia> dateplayed(g) == nothing
true
```
