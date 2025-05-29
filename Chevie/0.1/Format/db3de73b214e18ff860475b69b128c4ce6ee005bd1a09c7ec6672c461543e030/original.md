`showtable(io::IO=stdout, table::AbstractMatrix; keywords)`

General  routine to format a table at  the REPL, or in `IJulia` or `Pluto`. The elements of `table` and any of the labels in the keywords can be of any type  and are formatted in the context  of `io`, excepted that a string `s` is  formatted by  `fromTeX(io,s)`. The  following options  can be passed as properties of the `io` or as keywords.

  * `row_labels`: labels for rows. A `Vector{Any}` (can be strings), default `axes(table,1)`
  * `rows_label`: label for first column of row labels (default none)
  * `col_labels`: labels for other columns (default none)
  * `align`:  a character in "lcr": alignment of columns (default 'r'); then all columns will be aligned as given except the `rows_labels` which will always be aligned left. Or if `align` is a string it should be of length `1+size(table,2)` where the first character is the alignment of the `row_labels`.
  * `row_seps`: line numbers after which to put a separator. A number of `i` means before `i`-th line of the table. So `0` is at the top  of  the  table,  `-1`  is  before the `col_labels`. The default is `[-1,0,size(table,1)]`.
  * `col_seps`: column numbers after which to put a separator. A  number of `i` means before `i`-th column  of the table. So `0` is at the  left of the table, `-1` is before the `row_labels`. The default is `[-1,0,size(table,2)]`.  Alternately the `col_seps`  can be given using an  `align` string in  LaTeX style `|r|llll|`.  They should be given by only one of the two ways.
  * `rows`: show only these rows. Default all rows: `axes(table,1)`
  * `cols`: show only these columns. Default all columns: `axes(table,1)`
  * `TeX`: default `false`. If true, give LaTeX output (useful to give nicer output in Jupyter or Pluto)
  * `column_repartition`: a `Vector{<:Integer}`. Display in vertical pieces of sizes indicated (useful for `TeX`: otherwise the column_repartition is automatically computed taking in account `displaysize(io,2)`).
  * `dotzero`: if `true` replace a '0' by '.' in the table (default false).

```julia-rep1
julia> m=reshape(1:10:120,3,4)
3×4 reshape(::StepRange{Int64, Int64}, 3, 4) with eltype Int64:
  1  31  61   91
 11  41  71  101
 21  51  81  111

julia> showtable(m)
┌─┬────────────┐
│1│ 1 31 61  91│
│2│11 41 71 101│
│3│21 51 81 111│
└─┴────────────┘

julia> labels=["x","y","z","t"];

julia> showtable(m;cols=2:4,col_labels=labels,row_seps=[0,2,3])
    y  z   t 
┌─┬─────────┐
│1│31 61  91│
│2│41 71 101│
├─┼─────────┤
│3│51 81 111│
└─┴─────────┘

julia> showtable(m;col_labels=labels,rows_label="N",align="|r|ll|ll|")
┌─┬─────┬──────┐
│N│ x  y│ z   t│
├─┼─────┼──────┤
│1│1  31│61 91 │
│2│11 41│71 101│
│3│21 51│81 111│
└─┴─────┴──────┘
```
