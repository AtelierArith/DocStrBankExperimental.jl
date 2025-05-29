```
@intersect(sql_query1, sql_query2, all = false)
```

Combine two SQL queries/tables using `INTERSECT`

# Arguments

  * `sql_query1`: The first SQL query to combine.
  * `sql_query2`: The second SQL query to combine.
  * `all`: Defaults to false, when true it will return duplicates. `INTERSECT ALL`

# Returns

  * A lazy query of all rows in the second query bound to the first

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df1 = DataFrame(id = [1, 2, 2, 3, 4],
        name = ["Alice", "Bob", "Bob", "Charlie", "David"]);

julia> df2 = DataFrame( id = [2, 2, 3, 5],
       name = ["Bob", "Bob", "Charlie", "Eve"]);

julia> df1_table = dt(db, df1, "df1"); 

julia> df2_table = dt(db, df2, "df2"); 

julia> @chain df1_table @intersect(df2_table) @collect
2×2 DataFrame
 Row │ id     name    
     │ Int64  String  
─────┼────────────────
   1 │     2  Bob
   2 │     3  Charlie

julia> @chain df1_table @intersect(df2_table, all = true) @arrange(desc(id)) @collect
3×2 DataFrame
 Row │ id     name    
     │ Int64  String  
─────┼────────────────
   1 │     3  Charlie
   2 │     2  Bob
   3 │     2  Bob
```
