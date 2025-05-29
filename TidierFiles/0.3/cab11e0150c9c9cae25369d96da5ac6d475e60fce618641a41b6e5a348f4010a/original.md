```
read_delim(file; delim='	',col_names=true, skip=0, n_max=Inf, 
    comment=nothing, missing_value="", col_select, escape_double=true, col_types=nothing)
```

Reads a delimited file or URL into a DataFrame, with options to specify delimiter, column names, and other CSV parsing options.

# Arguments

  * `file`: Path or vector of paths to the CSV file or a URL to a CSV file.
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

julia> write_csv(df, "csvtest.csv");

julia> read_delim("csvtest.csv", delim = ",", col_names = false, num_threads = 4) # col_names are false here for the purpose of demonstration
6×3 DataFrame
 Row │ Column1  Column2  Column3 
     │ String3  String7  String7 
─────┼───────────────────────────
   1 │ ID       Name     Score
   2 │ 1        Alice    88
   3 │ 2        Bob      92
   4 │ 3        Charlie  77
   5 │ 4        David    85
   6 │ 5        Eva      95
```
