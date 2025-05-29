get_isfemale(filename::String)

Creates a `IsFemale` type/struct from control file in json format. If control file does not stipulate sex information, we assume all female  (*ref: [qtl2](https://github.com/rqtl/qtl2/blob/main/R/read_cross2.R)* line 229).

# Argument

  * `filename` : A string containing the name(with directory) of the control file in json format.

# Output

Returns a `IsFemale` type/struct.
