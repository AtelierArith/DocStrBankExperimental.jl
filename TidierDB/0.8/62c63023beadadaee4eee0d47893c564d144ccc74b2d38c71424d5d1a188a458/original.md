```
@union(sql_query1, sql_query2)
```

Combine two SQL queries using the `UNION ALL` operator.

# Arguments

  * `sql_query1`: The first SQL query to combine.
  * `sql_query2`: The second SQL query to combine.

# Returns

  * A lazy query of all rows in the second query bound to the first

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df1 = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> df1_table = dt(db, df1, "df1");

julia> @chain df1_table @union_all(df1_table) @collect
6×2 DataFrame
 Row │ id     value 
     │ Int64  Int64 
─────┼──────────────
   1 │     1     10
   2 │     2     20
   3 │     3     30
   4 │     1     10
   5 │     2     20
   6 │     3     30
```
