```
@left_join(sql_query, join_table, orignal_table_col == new_table_col)
```

Perform a left join between two SQL queries based on a specified condition.  Joins can be equi joins or inequality joins. For equi joins, the joining table  key column is dropped. Inequality joins can be made into AsOf or rolling joins  by wrapping the inequality in closest(key >= key2). With inequality joins, the  columns from both tables are kept. Multiple joining criteria can be added, but  need to be separated by commas, ie `closest(key >= key2), key3 == key3`

# Arguments

  * `sql_query::SQLQuery`: The primary SQL query to operate on.
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

julia> dfm = dt(db, df, "df_mem"); dfj = dt(db, df2, "df_join");

julia> @chain dfm begin
         @left_join(t(dfj), id == id2 )
         @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  category  score   
     │ String  String  Int64  Float64  String?   Int64?  
─────┼───────────────────────────────────────────────────
   1 │ AA      bb          1      0.1  X              88
   2 │ AC      bb          3      0.3  Y              92
   3 │ AE      bb          5      0.5  X              77
   4 │ AG      bb          2      0.7  Y              83
   5 │ AI      bb          4      0.9  X              95
   6 │ AB      aa          2      0.2  missing   missing 
   7 │ AD      aa          4      0.4  missing   missing 
   8 │ AF      aa          1      0.6  missing   missing 
   9 │ AH      aa          3      0.8  missing   missing 
  10 │ AJ      aa          5      1.0  missing   missing 

julia> query = @chain dt(db, "df_join") begin
                  @filter(score > 85) # only show scores above 85 in joining table
                end;

julia> @chain dfm begin
         @left_join(t(query), id == id2)
         @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  category  score   
     │ String  String  Int64  Float64  String?   Int64?  
─────┼───────────────────────────────────────────────────
   1 │ AA      bb          1      0.1  X              88
   2 │ AC      bb          3      0.3  Y              92
   3 │ AI      bb          4      0.9  X              95
   4 │ AB      aa          2      0.2  missing   missing 
   5 │ AD      aa          4      0.4  missing   missing 
   6 │ AE      bb          5      0.5  missing   missing 
   7 │ AF      aa          1      0.6  missing   missing 
   8 │ AG      bb          2      0.7  missing   missing 
   9 │ AH      aa          3      0.8  missing   missing 
  10 │ AJ      aa          5      1.0  missing   missing 

julia>  @chain dfm begin
         @mutate(test = percent * 100)
         @left_join(t(dfj), test <= score, id = id2)
         @collect
       end;


julia>  @chain dfm begin
         @mutate(test = percent * 200)
         @left_join(t(dfj), closest(test >= score)) # asof join
         @collect
       end;
```
