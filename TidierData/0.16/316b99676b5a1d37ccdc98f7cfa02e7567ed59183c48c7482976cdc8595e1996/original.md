```
@bind_cols(dfs...)
```

Bind many DataFrames into one by column. 

# Arguments

  * `dfs...`: DataFrames to combine.

# Examples

```jldoctest
julia> df1 = DataFrame(a=1:3, b=1:3);

julia> df2 = DataFrame(a=4:6, b=4:6);

julia> df3 = DataFrame(a=7:9, c=7:9);

julia> @chain df1 begin
         @bind_cols(df2, df3)
       end
3×6 DataFrame
 Row │ a      b      a_1    b_1    a_2    c     
     │ Int64  Int64  Int64  Int64  Int64  Int64 
─────┼──────────────────────────────────────────
   1 │     1      1      4      4      7      7
   2 │     2      2      5      5      8      8
   3 │     3      3      6      6      9      9
```
