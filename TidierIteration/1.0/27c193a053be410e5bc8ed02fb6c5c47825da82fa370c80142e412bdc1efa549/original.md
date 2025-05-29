```
map_dfc(x, f)
```

Apply the function `f` to each element of `x` and  bind all the columns into a dataframe.

# Arguments

  * `x`: an iterable collection.
  * `f`: a function that returns a DataFrame.

# Examples

```julia-repl
julia> map_dfc(1:3, x -> DataFrame(Symbol("a" * string(x)) => rand(3)))
3×3 DataFrame
 Row │ a1        a2        a3       
     │ Float64   Float64   Float64  
─────┼──────────────────────────────
   1 │ 0.864102  0.342032  0.99839
   2 │ 0.160245  0.912323  0.465663
   3 │ 0.235012  0.516522  0.368654
```
