```
@union(sql_query1, sql_query2, all = false)
```

Combine two SQL queries using the `UNION` operator.

# Arguments

  * `sql_query1`: The first SQL query to combine.
  * `sql_query2`: The second SQL query to combine.
  * `all`: Defaults to false, when true it will will return duplicates. `UNION ALL`

# Returns

  * A lazy query of all distinct rows in the second query bound to the first

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df1 = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> df2 = DataFrame(id = [4, 5, 6], value = [40, 50, 60]);

julia> df1_table = dt(db, df1, "df1");

julia> df2_table = dt(db, df2, "df2");

julia> @chain df1_table @union(df2_table) @collect
6×2 DataFrame
 Row │ id     value 
     │ Int64  Int64 
─────┼──────────────
   1 │     1     10
   2 │     2     20
   3 │     3     30
   4 │     4     40
   5 │     5     50
   6 │     6     60

julia> @chain df1_table begin 
        @union("df1", all = false)
        @collect
       end
3×2 DataFrame
 Row │ id     value 
     │ Int64  Int64 
─────┼──────────────
   1 │     1     10
   2 │     2     20
   3 │     3     30

julia> @chain df1_table begin 
        @union("df1", all = true) 
        @collect
       end
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

julia> query = @chain df2_table @filter(value == 50);

julia> @chain df1_table begin 
        @mutate(id = id + 5)
        @filter(id > 6)
        @union(t(query))
        @collect
       end
3×2 DataFrame
 Row │ id     value 
     │ Int64  Int64 
─────┼──────────────
   1 │     7     20
   2 │     8     30
   3 │     5     50
```
