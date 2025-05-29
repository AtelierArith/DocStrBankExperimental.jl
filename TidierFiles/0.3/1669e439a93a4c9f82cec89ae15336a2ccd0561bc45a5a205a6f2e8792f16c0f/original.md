```
fwf_empty(filepath::String; num_lines::Int=4, col_names=nothing)
```

Analyze a fixed-width format (FWF) file to automatically determine column widths and provide column names.

# Arguments

  * `filepath`::String: Path to the FWF file to analyze.

num_lines::Int=4: Number of lines to sample from the beginning of the file for analysis. Default is 4.

  * `col_names`: Optional; a vector of strings specifying column names. If not provided, column names are generated as Column*1, Column*2, etc.

# Returns

  * A tuple containing two elements:
  * A vector of integers representing the detected column widths.
  * A vector of strings representing the column names.

# Examples

```jldoctest
julia> fwf_data = 
       "John Smith   35    12345  Software Engineer   120,000 \nJane Doe     29     2345  Marketing Manager   95,000  \nAlice Jones  42   123456  CEO                 250,000 \nBob Brown    31    12345  Product Manager     110,000 \nCharlie Day  28      345  Sales Associate     70,000  \nDiane Poe    35    23456  Data Scientist      130,000 \nEve Stone    40   123456  Chief Financial Off 200,000 \nFrank Moore  33     1234  Graphic Designer    80,000  \nGrace Lee    27   123456  Software Developer  115,000 \nHank Zuse    45    12345  System Analyst      120,000 ";

julia> open("fwftest.txt", "w") do file
         write(file, fwf_data)
       end;

julia> path = "fwftest.txt";

julia> fwf_empty(path)
([13, 5, 8, 20, 8], ["Column_1", "Column_2", "Column_3", "Column_4", "Column_5"])

julia> fwf_empty(path, num_lines=4, col_names = ["Name", "Age", "ID", "Position", "Salary"])
([13, 5, 8, 20, 8], ["Name", "Age", "ID", "Position", "Salary"])
```
