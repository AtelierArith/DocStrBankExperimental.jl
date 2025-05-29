```
read_table(file; col_names=true, skip=0, n_max=Inf, comment=nothing, col_select, missing_value="", kwargs...)
```

Read a table from a file where columns are separated by any amount of whitespace, processing it into a DataFrame.

# Arguments

  * `file`: The path to the file to read.
  * `col_names`=true: Indicates whether the first non-skipped line should be treated as column names. If false, columns are named automatically.
  * `skip`: Number of lines at the beginning of the file to skip before processing starts.
  * `n_max`: The maximum number of lines to read from the file, after skipping. Inf means read all lines.
  * `col_select`: Optional vector of symbols or strings to select which columns to load.
  * `comment`: A character or string indicating the start of a comment. Lines starting with this character are ignored.
  * `missing_value`: The string that represents missing values in the table.
  * `kwargs`: Additional keyword arguments passed to CSV.File.

# Examples

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_table(df, "tabletest.txt");

julia> read_table("tabletest.txt", skip = 2, n_max = 3, col_select = ["Name"])
3×1 DataFrame
 Row │ Name    
     │ String7 
─────┼─────────
   1 │ Charlie
   2 │ David
   3 │ Eva

```
