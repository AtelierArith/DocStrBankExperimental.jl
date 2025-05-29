@separate(df, from, into, sep, extra = "merge")

Separate a string column into mulitiple new columns based on a specified delimter 

# Arguments

  * `df`: A DataFrame
  * `from`: Column that will be split
  * `into`: New column names, supports [] or ()
  * `sep`: the string or character on which to split
  * `extra`: "merge", "warn" and "drop" . If not enough columns are provided, extra determines whether additional entries will be merged into the final one or dropped. "warn" generates a warning message for dropped values.

# Examples

```jldoctest
julia> df = DataFrame(a = ["1-1", "2-2", "3-3-3"]);

julia> @separate(df, a, [b, c, d], "-")
3×3 DataFrame
 Row │ b          c          d          
     │ SubStrin…  SubStrin…  SubStrin…? 
─────┼──────────────────────────────────
   1 │ 1          1          missing    
   2 │ 2          2          missing    
   3 │ 3          3          3

julia> @chain df begin
         @separate(a, (b, c, d), "-")
       end
3×3 DataFrame
 Row │ b          c          d          
     │ SubStrin…  SubStrin…  SubStrin…? 
─────┼──────────────────────────────────
   1 │ 1          1          missing    
   2 │ 2          2          missing    
   3 │ 3          3          3

julia> @separate(df, a, (b, c), "-")
3×2 DataFrame
 Row │ b          c      
     │ SubStrin…  String 
─────┼───────────────────
   1 │ 1          1
   2 │ 2          2
   3 │ 3          3-3

julia> @chain df begin
         @separate(a, (b, c), "-", extra = "drop")
       end
3×2 DataFrame
 Row │ b          c         
     │ SubStrin…  SubStrin… 
─────┼──────────────────────
   1 │ 1          1
   2 │ 2          2
   3 │ 3          3

```

```
  @separate(sql_query, from_col, into_cols, sep)
```

Separate a string column into mulitiple new columns based on a specified delimter 

# Arguments

  * `sql_query`: The SQL query
  * `from_col`: Column that will be split
  * `into_cols`: New column names, supports [] or ()
  * `sep`: the string or character on which to split

# Examples

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(a = ["1-1", "2-2", "3-3-3"]); 

julia> @chain dt(db, df, "df") @separate(a, [b, c, d], "-") @collect
3×3 DataFrame
 Row │ b       c       d       
     │ String  String  String? 
─────┼─────────────────────────
   1 │ 1       1       missing 
   2 │ 2       2       missing 
   3 │ 3       3       3

julia> @chain dt(db, df, "df") @separate( a, [c, d], "-") @collect
3×2 DataFrame
 Row │ c       d      
     │ String  String 
─────┼────────────────
   1 │ 1       1
   2 │ 2       2
   3 │ 3       3-3
```
