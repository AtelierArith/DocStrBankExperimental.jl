```
@window_frame(sql_query, args...)
```

Define the window frame for window functions in a SQL query, specifying the range of rows to include in the calculation relative to the current row.

# Arguments

  * `sqlquery::SQLQuery`: The SQLQuery instance to which the window frame will be applied.
  * `args...`: A variable number of arguments specifying the frame boundaries. These can be:

      * `from`: The starting point of the frame. Can be a positive or negative integer, 0 or empty. When empty, it will use UNBOUNDED
      * `to`: The ending point of the frame. Can be a positive or negative integer,  0 or empty. When empty, it will use UNBOUNDED
      * if only one integer is provided without specifying `to` or `from` it will default to from, and to will be UNBOUNDED.
      * if no arguments are given, both will be UNBOUNDED

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> df_mem = dt(db, df, "df_view");

julia> @chain df_mem begin
        @group_by groups
        @window_frame(3)
        @mutate(avg = mean(percent))
        #@show_query
       end;

julia> @chain df_mem begin
        @group_by groups
        @window_frame(-3, 3)
        @mutate(avg = mean(percent))
        #@show_query
       end;

julia> @chain df_mem begin
        @group_by groups
        @window_frame(to = -3)
        @mutate(avg = mean(percent))
        #@show_query
        @collect
       end;

julia> @chain df_mem begin
        @group_by groups
        @window_frame(from = -3)
        @mutate(avg = mean(percent))
        #@show_query
        @collect
       end;
```
