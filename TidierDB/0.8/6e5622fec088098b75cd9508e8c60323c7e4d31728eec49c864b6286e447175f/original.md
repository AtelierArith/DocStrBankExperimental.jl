```
@transmute(sql_query, exprs...; _by, _frame, _order)
```

Transmute SQL table by adding new columns or modifying existing ones. Unlike `@mutate`, `@transmute` only keep columns on the left hand side of the `=`  in transmute or grouping.

# Arguments

  * `sql_query::SQLQuery`: The SQL query to operate on.
  * `exprs`: Expressions for mutating the table. New columns can be added or existing columns modified using `column_name = expression syntax`, where expression can involve existing columns.
  * `_by`: optional argument that supports single column names, or vectors of columns to allow for grouping for the transformation in the macro call
  * `_frame`: optional argument that allows window frames to be determined within `@mutate`. supports single digits or tuples of numbers. supports `desc()` prefix
  * `_order`: optional argument that allows window orders to be determined within `@mutate`. supports single columns or vectors of names

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @transmute(value = value * 4, new_col = percent^2)
         @collect
       end
10×2 DataFrame
 Row │ value  new_col 
     │ Int64  Float64 
─────┼────────────────
   1 │     4     0.01
   2 │     8     0.04
   3 │    12     0.09
   4 │    16     0.16
   5 │    20     0.25
   6 │     4     0.36
   7 │     8     0.49
   8 │    12     0.64
   9 │    16     0.81
  10 │    20     1.0

julia> @chain dt(db, df, "df_view") begin
         @transmute(max = maximum(value), _by = groups)
         @collect
       end
10×2 DataFrame
 Row │ groups  max   
     │ String  Int64 
─────┼───────────────
   1 │ aa          5
   2 │ aa          5
   3 │ aa          5
   4 │ aa          5
   5 │ aa          5
   6 │ bb          5
   7 │ bb          5
   8 │ bb          5
   9 │ bb          5
  10 │ bb          5
```
