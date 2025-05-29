```
read_meta(fn, group)
```

Read in a meta data file with the first row assumed to be the header and the row names assumed to be the profile names (cell barcodes). Grouping information is specified by the column with the header name of `group`. If `group` is not found, the second column will be used. It returns the grouped profile names (vector of vectors) and group names.

# Examples

```jldoctest

julia> grp, nam = read_meta("meta.tsv", "Cluster")

julia> length(grp)
12

julia> length.(grp)
12-element Vector{Int64}:
   65
  512
 1057
  647
  654
  326
  680
  369
 1191
   46
  101
   80

julia> length(nam)
12
```
