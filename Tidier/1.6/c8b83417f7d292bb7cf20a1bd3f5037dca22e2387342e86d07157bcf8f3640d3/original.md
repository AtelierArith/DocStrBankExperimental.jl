```
@rename(df, exprs...)
```

Change the names of individual column names in a DataFrame. Users can also use `@select()` to rename and select columns.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: Use `new_name = old_name` syntax to rename selected columns.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @rename(d = b, e = c)
       end
5×3 DataFrame
 Row │ a     d      e     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         2     12
   3 │ c         3     13
   4 │ d         4     14
   5 │ e         5     15
```

```
@rename(sql_query, renamings...)
```

Rename one or more columns in a SQL query.

# Arguments

-`sql_query`: The SQL query to operate on. -`renamings`: One or more pairs of old and new column names, specified as new name = old name 

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
       @rename(new_name = percent)
       @collect
       end
10×4 DataFrame
 Row │ id      groups  value  new_name 
     │ String  String  Int64  Float64  
─────┼─────────────────────────────────
   1 │ AA      bb          1       0.1
   2 │ AB      aa          2       0.2
   3 │ AC      bb          3       0.3
   4 │ AD      aa          4       0.4
   5 │ AE      bb          5       0.5
   6 │ AF      aa          1       0.6
   7 │ AG      bb          2       0.7
   8 │ AH      aa          3       0.8
   9 │ AI      bb          4       0.9
  10 │ AJ      aa          5       1.0
```
