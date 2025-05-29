```
function pivot()
```

長形式のDataFrame `df` を広形式のDataFrame `B` として表現します。

オプション引数 `x` と `y` は `df` の列です。単一の列 `x` （デフォルトでは `df` の最初の列）は `B` の行名になります。列 `y` （デフォルトでは `x` 以外のすべての列）は `B` の列名になります。

# 例

```jldoctest
julia> using DataFrames

julia> df = DataFrame(name=["Cookie Monster", "Elmo", "Oscar", "Grover"], fur_color=["blue", "red", "green", "blue"])
4×2 DataFrame
 Row │ name            fur_color
     │ String          String
─────┼───────────────────────────
   1 │ Cookie Monster  blue
   2 │ Elmo            red
   3 │ Oscar           green
   4 │ Grover          blue

julia> pivot(df)
4×4 DataFrame
 Row │ name            blue   red    green
     │ String          Bool   Bool   Bool
─────┼─────────────────────────────────────
   1 │ Cookie Monster   true  false  false
   2 │ Elmo            false   true  false
   3 │ Oscar           false  false   true
   4 │ Grover           true  false  false

```
