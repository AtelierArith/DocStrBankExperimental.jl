```
writedlm2(f, A; opts...)
writedlm2(f, A, delim; opts...)
```

Write `A` (a vector, matrix, or an iterable collection of iterable rows, a `Tables` source) as text to `f` (either a filename or an IO stream). The columns are separated by `';'`, another `delim` (Char or String) can be defined.

By default, a pre-processing of values takes place. Before writing as strings, decimal marks are changed from `'.'` to `','`. With the keyword argument `decimal=` another decimal mark can be defined. To switch off this pre-processing set: `decimal='.'`.

In `writedlm2()` the output format for `Date` and `DateTime` data can be defined with format strings. Defaults are the ISO formats. Day (`E`, `e`) and month (`U`, `u`) names are written in the `locale` language. For writing `Complex` numbers the imaginary component suffix can be selected with the `imsuffix=` keyword argument.

# Additional Keyword Arguments

  * `decimal=','`: Character for writing decimal marks
  * `dtfs="yyyy-mm-ddTHH:MM:SS.s"`: DateTime write format
  * `dfs="yyyy-mm-dd"`: Date write format
  * `locale="english"`: Language for DateTime writing
  * `imsuffix="im"`: Complex Imag suffix `"im"`, `"i"` or `"j"`
  * `missingstring="na"`: How missing values are written

# Code Example

```jldoctest
julia> using ReadWriteDlm2, Dates

julia> A = Any[1 1.2; "text" Date(2017)];

julia> writedlm2("test.csv", A)

julia> read("test.csv", String)
"1;1,2\ntext;2017-01-01\n"
```
