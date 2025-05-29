```
read_tsv(file; delim='	',col_names=true, skip=0, n_max=Inf, 
    comment=nothing, missing_value="", col_select, escape_double=true, col_types=nothing)
```

Reads a TSV file or URL into a DataFrame, with options to specify delimiter, column names, and other CSV parsing options.

# Arguments

  * `file`: Path or vector of paths to the TSV file or a URL to a TSV file.
  * `delim`: The character delimiting fields in the file. Default is ','.
  * `decimal`: Character argument for what character decimal should be. Default is `.`
  * `col_names`: Indicates if the first row of the CSV is used as column names. Can be true, false, or an array of strings. Default is true.
  * `skip`: Number of initial lines to skip before reading data. Default is 0.
  * `n_max`: Maximum number of rows to read. Default is Inf (read all rows).
  * `col_select`: Optional vector of symbols or strings to select which columns to load.
  * `comment`: Character that starts a comment line. Lines beginning with this character are ignored. Default is nothing (no comment lines).
  * `col_types`: Optional Dict to allow for column type specification
  * `missing_value`: String that represents missing values in the CSV. Default is "", can be set to a vector of multiple items.
  * `escape_double`: Indicates whether to interpret two consecutive quote characters as a single quote in the data. Default is true.
  * `num_threads`: specifies the number of concurrent tasks or threads to use for processing, allowing for parallel execution. Default is the number of available threads.

# Examples

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_tsv(df, "tsvtest.tsv");

julia> read_tsv("tsvtest.tsv", skip = 2, n_max = 3, missing_value = ["Charlie"])
3×3 DataFrame
 Row │ ID     Name      Score 
     │ Int64  String7?  Int64 
─────┼────────────────────────
   1 │     3  missing      77
   2 │     4  David        85
   3 │     5  Eva          95
```
