```
   @summary(sql_query)
```

Get summary stastics on a table or a file when using DuckDB (max, min, q1, q2, q3, avg, std, count, unique)

# Arguments

  * `sql_query`: The SQL table or file to summarize

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
        @summary
        @collect
       end;
```
