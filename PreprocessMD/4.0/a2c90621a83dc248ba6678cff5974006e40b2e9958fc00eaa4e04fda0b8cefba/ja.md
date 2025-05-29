```
function top_n_values(df::AbstractDataFrame, col::Union{String, Symbol}, n::Int)::AbstractDataFrame
```

出現回数による上位 n 値を見つける 初期の実現可能性チェックに便利ですが、医療コードは考慮されません

# 例

```jldoctest
julia> using DataFrames

julia> df = DataFrame(name=["Cookie Monster", "Elmo", "Oscar", "Grover", "Big Bird", "Ernie", "Bert", "Rosita"], fur_color=["blue", "red", "green", "blue", "yellow", "orange", "yellow", "blue"])
8×2 DataFrame
 Row │ name            fur_color
     │ String          String
─────┼───────────────────────────
   1 │ Cookie Monster  blue
   2 │ Elmo            red
   3 │ Oscar           green
   4 │ Grover          blue
   5 │ Big Bird        yellow
   6 │ Ernie           orange
   7 │ Bert            yellow
   8 │ Rosita          blue

julia> top_n_values(df, :fur_color, 4)
4×2 DataFrame
 Row │ fur_color  nrow
     │ String     Int64
─────┼──────────────────
   1 │ blue           3
   2 │ yellow         2
   3 │ red            1
   4 │ green          1

```
