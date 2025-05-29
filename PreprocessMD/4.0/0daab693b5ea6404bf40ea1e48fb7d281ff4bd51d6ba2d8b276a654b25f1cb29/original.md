```
function pivot()
```

Express the long format DataFrame `df` as a wide format DataFrame `B`.

Optional arguments `x` and `y` are columns of `df`. The single column `x` (the first column of `df`, by default) becomes the row names of `B`. Column(s) `y` (all columns besides `x`, by default) become the column names of `B`.

# Examples

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
