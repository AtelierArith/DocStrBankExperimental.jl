```
@inner_join(df1, df2, [by])
```

Perform a inner join on `df1` and `df2` with an optional `by`.

# Arguments

  * `df1`: A DataFrame.
  * `df2`: A DataFrame.
  * `by`: An optional column or tuple of columns. `by` supports interpolation of individual columns. If `by` is not supplied, then it will be inferred from shared names of columns between `df1` and `df2`.

# Examples

```jldoctest
julia> df1 = DataFrame(a = ["a", "b"], b = 1:2);

julia> df2 = DataFrame(a = ["a", "c"], c = 3:4);
  
julia> @inner_join(df1, df2)
1×3 DataFrame
 Row │ a       b      c     
     │ String  Int64  Int64 
─────┼──────────────────────
   1 │ a           1      3

julia> @inner_join(df1, df2, a)
1×3 DataFrame
 Row │ a       b      c     
     │ String  Int64  Int64 
─────┼──────────────────────
   1 │ a           1      3

julia> @inner_join(df1, df2, a = a)
1×3 DataFrame
 Row │ a       b      c     
     │ String  Int64  Int64 
─────┼──────────────────────
   1 │ a           1      3

julia> @inner_join(df1, df2, "a")
1×3 DataFrame
 Row │ a       b      c     
     │ String  Int64  Int64 
─────┼──────────────────────
   1 │ a           1      3

julia> @inner_join(df1, df2, "a" = "a")
1×3 DataFrame
 Row │ a       b      c     
     │ String  Int64  Int64 
─────┼──────────────────────
   1 │ a           1      3
```
