```
read_files(path; args)
```

Generic file reader that automatically detects type and dispatches the appropriate read function. 

# Arguments

  * `path` : a string with the file path to read
  * `args` : additional arguments supported for that specific file type are given as they normally would be

# Examples

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_parquet(df, "test.parquet");

julia> read_file("test.parquet")
5×3 DataFrame
 Row │ ID     Name     Score 
     │ Int64  String   Int64 
─────┼───────────────────────
   1 │     1  Alice       88
   2 │     2  Bob         92
   3 │     3  Charlie     77
   4 │     4  David       85
   5 │     5  Eva         95
```
