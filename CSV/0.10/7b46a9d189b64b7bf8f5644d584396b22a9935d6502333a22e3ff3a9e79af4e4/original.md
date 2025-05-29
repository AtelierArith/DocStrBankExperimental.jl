```
CSV.write(file, table; kwargs...) => file
table |> CSV.write(file; kwargs...) => file
```

Write a [Tables.jl interface input](https://github.com/JuliaData/Tables.jl) to a csv file, given as an `IO` argument or `String`/FilePaths.jl type representing the file name to write to. Alternatively, `CSV.RowWriter` creates a row iterator, producing a csv-formatted string for each row in an input table.

Supported keyword arguments include:

  * `bufsize::Int=2^22`: The length of the buffer to use when writing each csv-formatted row; default 4MB; if a row is larger than the `bufsize` an error is thrown
  * `delim::Union{Char, String}=','`: a character or string to print out as the file's delimiter
  * `quotechar::Char='"'`: ascii character to use for quoting text fields that may contain delimiters or newlines
  * `openquotechar::Char`: instead of `quotechar`, use `openquotechar` and `closequotechar` to support different starting and ending quote characters
  * `escapechar::Char='"'`: ascii character used to escape quote characters in a text field
  * `missingstring::String=""`: string to print for `missing` values
  * `dateformat=Dates.default_format(T)`: the date format string to use for printing out `Date` & `DateTime` columns
  * `append=false`: whether to append writing to an existing file/IO, if `true`, it will not write column names by default
  * `compress=false`: compress the written output using standard gzip compression (provided by the CodecZlib.jl package); note that a compression stream can always be provided as the first "file" argument to support other forms of compression; passing `compress=true` is just for convenience to avoid needing to manually setup a GzipCompressorStream
  * `writeheader=!append`: whether to write an initial row of delimited column names, not written by default if appending
  * `header`: pass a list of column names (Symbols or Strings) to use instead of the column names of the input table
  * `newline='\n'`: character or string to use to separate rows (lines in the csv file)
  * `quotestrings=false`: whether to force all strings to be quoted or not
  * `decimal='.'`: character to use as the decimal point when writing floating point numbers
  * `transform=(col,val)->val`: a function that is applied to every cell e.g. we can transform all `nothing` values to `missing` using `(col, val) -> something(val, missing)`
  * `bom=false`: whether to write a UTF-8 BOM header (0xEF 0xBB 0xBF) or not
  * `partition::Bool=false`: by passing `true`, the `table` argument is expected to implement `Tables.partitions` and the `file` argument can either be an indexable collection of `IO`, file `String`s, or a single file `String` that will have an index appended to the name

## Examples

```julia
using CSV, Tables, DataFrames

# write out a DataFrame to csv file
df = DataFrame(rand(10, 10), :auto)
CSV.write("data.csv", df)

# write a matrix to an in-memory IOBuffer
io = IOBuffer()
mat = rand(10, 10)
CSV.write(io, Tables.table(mat))
```
