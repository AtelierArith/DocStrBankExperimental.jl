```
@select(df, exprs...)
```

Select variables in a DataFrame.

# Arguments

  * `df`: A DataFrame.
  * `exprs...`: One or more unquoted variable names separated by commas. Variable names         can also be used as their positions in the data, like `x:y`, to select         a range of variables.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df @select(a, b, c)
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         2     12
   3 │ c         3     13
   4 │ d         4     14
   5 │ e         5     15

julia> @chain df @select(a:b)
5×2 DataFrame
 Row │ a     b     
     │ Char  Int64 
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3
   4 │ d         4
   5 │ e         5

julia> @chain df @select(1:2)
5×2 DataFrame
 Row │ a     b     
     │ Char  Int64 
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3
   4 │ d         4
   5 │ e         5

julia> @chain df @select(-(a:b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(!(a:b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(-(a, b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(!(a, b))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df begin
         @select(contains("b"), starts_with("c"))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df @select(-(1:2))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(!(1:2))
5×1 DataFrame
 Row │ c     
     │ Int64 
─────┼───────
   1 │    11
   2 │    12
   3 │    13
   4 │    14
   5 │    15

julia> @chain df @select(-c)
5×2 DataFrame
 Row │ a     b     
     │ Char  Int64 
─────┼─────────────
   1 │ a         1
   2 │ b         2
   3 │ c         3
   4 │ d         4
   5 │ e         5

julia> @chain df begin
         @select(-contains("a"))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
   
julia> @chain df begin
         @select(!contains("a"))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df begin
         @select(where(is_number))
       end
5×2 DataFrame
 Row │ b      c     
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
```

```
@select(sql_query, columns)
```

Select specified columns from a SQL table.

# Arguments

  * `sql_query::SQLQuery`: the SQL query to select columns from.
  * `columns`: Expressions specifying the columns to select. Columns can be specified by        - name, `table.name`       - selectors - `starts_with()`        - ranges - `col1:col5`       - excluded with `!` notation

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> df_mem = dt(db, df, "df_view");

julia> @chain df_mem begin
         @select(groups:percent)
         @collect
       end
10×3 DataFrame
 Row │ groups  value  percent 
     │ String  Int64  Float64 
─────┼────────────────────────
   1 │ bb          1      0.1
   2 │ aa          2      0.2
   3 │ bb          3      0.3
   4 │ aa          4      0.4
   5 │ bb          5      0.5
   6 │ aa          1      0.6
   7 │ bb          2      0.7
   8 │ aa          3      0.8
   9 │ bb          4      0.9
  10 │ aa          5      1.0

julia> @chain df_mem begin
         @select(contains("e"))
         @collect
       end
10×2 DataFrame
 Row │ value  percent 
     │ Int64  Float64 
─────┼────────────────
   1 │     1      0.1
   2 │     2      0.2
   3 │     3      0.3
   4 │     4      0.4
   5 │     5      0.5
   6 │     1      0.6
   7 │     2      0.7
   8 │     3      0.8
   9 │     4      0.9
  10 │     5      1.0
```
