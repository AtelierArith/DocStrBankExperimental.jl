```
write_parquet(df, )
```

Write a DataFrame to an Parquet (.parquet) file.

# Arguments

  * `df`: The DataFrame to be written to a file.
  * `path`: String as path where the .dta file will be created. If a file at this path already exists, it will be overwritten.

# Examples

```jldoctest
julia> df = DataFrame(AA=["Par", "quet"], AB=[10.1, 10.2]);

julia> write_parquet(df, "test.parquet");
```
