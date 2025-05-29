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
