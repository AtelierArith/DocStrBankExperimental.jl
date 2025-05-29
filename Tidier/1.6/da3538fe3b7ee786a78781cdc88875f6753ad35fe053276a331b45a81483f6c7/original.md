```
   @summary(df, cols...)
```

For numerical columns, returns a dataframe with the Q1,Q3, min, max, mean, median, number of missing values

# Arguments

  * 'df': A DataFrame
  * `cols`: columns on which summary will be performed. This is an optional arguement, without which summary will be performed on all numerical columns

# Examples

```jldoctest
julia> df = DataFrame(a = [1, 2, 3, 4, 5],
                      b = [missing, 7, 8, 9, 10],
                      c = [11, missing, 13, 14, missing],
                      d = [16.1, 17.2, 18.3, 19.4, 20.5],
                      e = ["a", "a", "a", "a", "a"]);

julia> @summary(df);

julia> @summary(df, (b:d));

julia> @chain df begin
         @summary(b:d)
       end;
```

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
