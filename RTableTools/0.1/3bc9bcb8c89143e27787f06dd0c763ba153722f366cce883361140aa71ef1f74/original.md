```
expand_grid(; kw...)
```

Create a Data Frame from All Combinations of Factor Variables (see R's base::expand.grid)

# Return

A DataFrame containing one row for each combination of the supplied argument. The first factors vary fastest.

# Examples

```julia
julia> dims = (x = 1:2, y = [3, 4], z = ["a", "b", "c"]);

julia> expand_grid(;dims...)
12×3 DataFrame
 Row │ x      y      z      
     │ Int64  Int64  String 
─────┼──────────────────────
   1 │     1      3  a
   2 │     2      3  a
   3 │     1      4  a
   4 │     2      4  a
   5 │     1      3  b
   6 │     2      3  b
   7 │     1      4  b
   8 │     2      4  b
   9 │     1      3  c
  10 │     2      3  c
  11 │     1      4  c
  12 │     2      4  c
```
