```
@slice_sample(sql_query, n)
```

Randomly select a specified number of rows from a SQL table.

# Arguments

  * `sql_query::SQLQuery`: The SQL query to sample
  * `n`: The number of rows to randomly select.

# Examples

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @slice_sample(n = 2)
         @collect
       end;

julia> @chain dt(db, df, "df_view") begin
       @slice_sample()
       @collect
       end;
```
