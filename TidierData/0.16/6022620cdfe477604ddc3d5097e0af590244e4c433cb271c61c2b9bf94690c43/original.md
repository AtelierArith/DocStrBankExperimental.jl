```
@slice_sample(df, [n = 1, prop, replace = false])
```

Randomly sample rows from a DataFrame `df` or from each group in a GroupedDataFrame. The default is to return 1 row. Either the number of rows (`n`) or the proportion of rows (`prop`) should be provided as a keyword argument.

# Arguments

  * `df`: The source data frame or grouped data frame from which to sample rows.
  * `n`: The number of rows to sample. Defaults to `1`.
  * `prop`: The proportion of rows to sample.
  * `replace`: Whether to sample with replacement. Defaults to `false`.

# Examples

```julia
julia> df = DataFrame(a = 1:10, b = 11:20);

julia> using StableRNGs, Random

julia> rng = StableRNG(1);

julia> Random.seed!(rng, 1);

julia> @chain df begin 
         @slice_sample(n = 5)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     6     16
   2 │     1     11
   3 │     5     15
   4 │     4     14
   5 │     8     18

julia> @chain df begin 
         @slice_sample(n = 5, replace = true)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     7     17
   2 │     2     12
   3 │     1     11
   4 │     4     14
   5 │     2     12

julia> @chain df begin 
         @slice_sample(prop = 0.5)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     6     16
   2 │     7     17
   3 │     5     15
   4 │     9     19
   5 │     2     12

julia> @chain df begin 
         @slice_sample(prop = 0.5, replace = true)
       end
5×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │    10     20
   2 │     4     14
   3 │     9     19
   4 │     9     19
   5 │     8     18
```
