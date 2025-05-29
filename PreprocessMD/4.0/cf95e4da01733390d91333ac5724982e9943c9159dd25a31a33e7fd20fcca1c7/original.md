```
function subsetMD(main_df, check_df, main_id, check_id)
```

Filtration step

# Arguments

  * `main_df::AbstractDataFrame`: Rows are selected from this DataFrame...
  * `check_df::AbstractDataFrame`: ... if the IDs are present in this DataFrame
  * `main_id`: ID column from `main_df` (Default: first column)
  * `check_id`: ID column from `check_df` (Default: same as `main_id`)

# Examples

```jldoctest
julia> using DataFrames

julia> X = DataFrame(name=["Cookie Monster", "Elmo", "Oscar", "Grover"], blue = [true, false, false, true], red  = [false, true, false, false], green = [false, false, true, false])
4×4 DataFrame
 Row │ name            blue   red    green
     │ String          Bool   Bool   Bool
─────┼─────────────────────────────────────
   1 │ Cookie Monster   true  false  false
   2 │ Elmo            false   true  false
   3 │ Oscar           false  false   true
   4 │ Grover           true  false  false

julia> Y = DataFrame(name=["Big Bird", "Cookie Monster", "Elmo"], fuzzy=[false, true, true])
3×2 DataFrame
 Row │ name            fuzzy
     │ String          Bool
─────┼───────────────────────
   1 │ Big Bird        false
   2 │ Cookie Monster   true
   3 │ Elmo             true

julia> subsetMD(X,Y)
2×4 DataFrame
 Row │ name            blue   red    green
     │ String          Bool   Bool   Bool
─────┼─────────────────────────────────────
   1 │ Cookie Monster   true  false  false
   2 │ Elmo            false   true  false

```
