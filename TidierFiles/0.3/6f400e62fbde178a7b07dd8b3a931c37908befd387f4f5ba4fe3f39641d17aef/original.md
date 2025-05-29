```
read_fwf(filepath::String; num_lines::Int=4, col_names=nothing)
```

Read fixed-width format (FWF) files into a DataFrame.

# Arguments

  * `filepath`::String: Path to the FWF file to read.
  * `widths_colnames`::Tuple{Vector{Int}, Union{Nothing, Vector{String}}}: A tuple containing two elements:       - A vector of integers specifying the widths of each field.       - Optionally, a vector of strings specifying column names. If nothing, column names are generated as Column*1, Column*2, etc.
  * `skip_to`=0: Number of lines at the beginning of the file to skip before reading data.
  * `n_max`=nothing: Maximum number of lines to read from the file. If nothing, read all lines.

# Examples

```jldoctest
julia> fwf_data = 
       "John Smith   35    12345  Software Engineer   120,000 \nJane Doe     29     2345  Marketing Manager   95,000  \nAlice Jones  42   123456  CEO                 250,000 \nBob Brown    31    12345  Product Manager     110,000 \nCharlie Day  28      345  Sales Associate     70,000  \nDiane Poe    35    23456  Data Scientist      130,000 \nEve Stone    40   123456  Chief Financial Off 200,000 \nFrank Moore  33     1234  Graphic Designer    80,000  \nGrace Lee    27   123456  Software Developer  115,000 \nHank Zuse    45    12345  System Analyst      120,000 ";

julia> open("fwftest.txt", "w") do file
         write(file, fwf_data)
       end;

julia> path = "fwftest.txt";

julia> read_fwf(path, fwf_empty(path, num_lines=4, col_names = ["Name", "Age", "ID", "Position", "Salary"]), skip_to=3, n_max=3)
3×5 DataFrame
 Row │ Name         Age     ID      Position         Salary  
     │ String       String  String  String           String  
─────┼───────────────────────────────────────────────────────
   1 │ Bob Brown    31      12345   Product Manager  110,000
   2 │ Charlie Day  28      345     Sales Associate  70,000
   3 │ Diane Poe    35      23456   Data Scientist   130,000
```
