```
map_dfr(x, f)
```

Apply the function `f` to each element of `x` and  bind all the rows into a dataframe.

# Arguments

  * `x`: an iterable collection.
  * `f`: a function that returns a DataFrame.

# Examples

```julia-repl
julia> map_dfr(1:3, x -> DataFrame(a = rand(3)))
9×1 DataFrame
 Row │ a         
     │ Float64   
─────┼───────────
   1 │ 0.719786
   2 │ 0.208629
   3 │ 0.689885
   4 │ 0.334989
   5 │ 0.0575872
   6 │ 0.0717808
   7 │ 0.825819
   8 │ 0.289853
   9 │ 0.495595
```
