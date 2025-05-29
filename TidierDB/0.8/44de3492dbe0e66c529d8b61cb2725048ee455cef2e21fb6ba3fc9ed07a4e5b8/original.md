```
   @window_order(sql_query, columns...)
```

Specify the order of rows for window functions within a SQL query.

# Arguments

  * `sql_query`: The SQL query to operate on.
  * `columns`: Columns to order the rows by for the window function. Can include multiple columns for nested sorting. Prepend a column name with - for descending order.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
        @group_by groups
        @window_frame(3)
        @window_order(desc(percent))
        @mutate(avg = mean(value))
       #@show_query 
       end;
```
