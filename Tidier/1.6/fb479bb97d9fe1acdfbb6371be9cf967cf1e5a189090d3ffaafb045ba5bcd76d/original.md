```
@anti_join(df1, df2, [by])
```

Perform an anti-join on `df1` and `df2` with an optional `by`.

# Arguments

  * `df1`: A DataFrame.
  * `df2`: A DataFrame.
  * `by`: An optional column or tuple of columns. `by` supports interpolation of individual columns. If `by` is not supplied, then it will be inferred from shared names of columns between `df1` and `df2`.

# Examples

```jldoctest
julia> df1 = DataFrame(a = ["a", "b"], b = 1:2);

julia> df2 = DataFrame(a = ["a", "c"], c = 3:4);
  
julia> @anti_join(df1, df2)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, a)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, a = a)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, "a")
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, "a" = "a")
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2
```

```
@anti_join(sql_query, join_table, orignal_table_col == new_table_col)
```

Perform an anti join between two SQL queries based on a specified condition.  Joins can be equi joins or inequality joins. For equi joins, the joining table  key column is dropped. Inequality joins can be made into AsOf or rolling joins  by wrapping the inequality in closest(key >= key2). With inequality joins, the  columns from both tables are kept. Multiple joining criteria can be added, but  need to be separated by commas, ie `closest(key >= key2), key3 == key3`

# Arguments

  * `sql_query`: The primary SQL query to operate on.
  * `join_table::{SQLQuery, String}`: The secondary SQL table to join with the primary query table. Table that exist on the database already should be written as a string of the name
  * `orignal_table_col`: Column from the original table that matches for join.  Accepts cols as bare column names or strings
  * `new_table_col`: Column from the new table that matches for join.  Accepts cols as bare column names or strings

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> df2 = DataFrame(id2 = ["AA", "AC", "AE", "AG", "AI", "AK", "AM"],
                category = ["X", "Y", "X", "Y", "X", "Y", "X"],
                score = [88, 92, 77, 83, 95, 68, 74]);

julia> db = connect(duckdb());


julia> dfj = dt(db, df2, "df_join");

julia> @chain dt(db, df, "df_view") begin
        @anti_join(t(dfj), id == id2)
        @collect
       end
5×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AB      aa          2      0.2
   2 │ AD      aa          4      0.4
   3 │ AF      aa          1      0.6
   4 │ AH      aa          3      0.8
   5 │ AJ      aa          5      1.0
```
