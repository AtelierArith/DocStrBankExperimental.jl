@pivot*longer(df, cols, [names*to], [values_to])

Reshapes the DataFrame to make it longer, increasing the number of rows and reducing the number of columns.

# Arguments

  * `df`: A DataFrame.
  * `cols`: Columns to pivot into longer format. Multiple columns can be selected but providing tuples of columns is not yet supported.
  * `names_to`: Optional, defaults to `variable`. The name of the newly created column whose values will contain the input DataFrame's column names.
  * `values_to`: Optional, defaults to `value`. The name of the newly created column containing the input DataFrame's cell values.

# Examples

```jldoctest
julia> df_wide = DataFrame(id = [1, 2], A = [1, 3], B = [2, 4]);

julia> @pivot_longer(df_wide, A:B)
4×3 DataFrame
 Row │ id     variable  value 
     │ Int64  String    Int64
─────┼────────────────────────
   1 │     1  A             1
   2 │     2  A             3
   3 │     1  B             2
   4 │     2  B             4

julia> @pivot_longer(df_wide, -id)
4×3 DataFrame
 Row │ id     variable  value 
     │ Int64  String    Int64
─────┼────────────────────────
   1 │     1  A             1
   2 │     2  A             3
   3 │     1  B             2
   4 │     2  B             4

julia> @pivot_longer(df_wide, A:B, names_to = "letter", values_to = "number")
4×3 DataFrame
 Row │ id     letter  number 
     │ Int64  String  Int64
─────┼───────────────────────
   1 │     1  A            1
   2 │     2  A            3
   3 │     1  B            2
   4 │     2  B            4

julia> @pivot_longer(df_wide, A:B, names_to = letter, values_to = number)
4×3 DataFrame
 Row │ id     letter  number 
     │ Int64  String  Int64
─────┼───────────────────────
   1 │     1  A            1
   2 │     2  A            3
   3 │     1  B            2
   4 │     2  B            4

julia> @pivot_longer(df_wide, A:B, names_to = "letter")
4×3 DataFrame
 Row │ id     letter  value 
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  A           1
   2 │     2  A           3
   3 │     1  B           2
   4 │     2  B           4

```

@pivot*longer(df, names*from, values_from)

Reshapes the SQL_query to make it longer, increasing the number of rows and reducing the number of columns.

# Arguments

  * `sql_query`: The SQL query
  * `cols`: Columns to pivot into longer format. Multiple columns can be selected
  * `names_from`: Optional, defaults to variable. The name of the newly created column whose values will contain the input DataFrame's column names.
  * `values_from`:  Optional, defaults to value. The name of the newly created column containing the input DataFrame's cell values.

# Examples

```jldoctest
julia> df = DataFrame(id = [1, 2], A = [1, 3], B = [2, 4]);

julia> db = connect(duckdb()); df_wide = dt(db, df, "df");

julia> @collect @pivot_longer(df_wide, A:B)
4×3 DataFrame
 Row │ id     variable  value 
     │ Int64  String    Int64 
─────┼────────────────────────
   1 │     1  A             1
   2 │     2  A             3
   3 │     1  B             2
   4 │     2  B             4

julia> @collect @pivot_longer(df_wide, A:B, names_to = "letter", values_to = "number")
4×3 DataFrame
 Row │ id     letter  number 
     │ Int64  String  Int64  
─────┼───────────────────────
   1 │     1  A            1
   2 │     2  A            3
   3 │     1  B            2
   4 │     2  B            4
```
