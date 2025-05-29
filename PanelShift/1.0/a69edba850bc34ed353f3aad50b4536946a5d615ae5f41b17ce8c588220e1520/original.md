```
panellead!(df, id, t, x, newx, n=oneunit(df[1, t] - df[1, t]); checksorted=true)
```

Within dataframe `df`, for each group indexed by `id`, lead (forward) column `x` by `n` periods with respect to the time column `t` using `tlag`, and store the forwarded column under the name `newx`. Arguments `id`, `t`, `x`, and `newx` are all column indicies in `df`.

# Examples

```jldoctest
julia> using DataFrames;
julia> df = DataFrame(
    t = [1;2;3;4; 1;3;4; 1;4; 1], 
    id = [1;1;1;1; 2;2;2; 3;3; 4],
    x = [1;2;3;4; 5;6;7; 8;9; 10]
);
julia> panellead!(df, :id, :t, :x, :Fx)

10×4 DataFrame
 Row │ t      id     x      Fx      
     │ Int64  Int64  Int64  Int64?  
─────┼──────────────────────────────
   1 │     1      1      1  missing 
   2 │     2      1      2        1
   3 │     3      1      3        2
  ⋮  │   ⋮      ⋮      ⋮       ⋮
   8 │     1      3      8  missing 
   9 │     4      3      9  missing 
  10 │     1      4     10  missing 
                      4 rows omitted
```
