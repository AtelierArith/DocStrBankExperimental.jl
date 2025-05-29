```
SummarizedExperiment(assays, rowdata, coldata, metadata = Dict{String,Any}())
```

Create an instance of a `SummarizedExperiment` with the supplied assays and the row/column annotations.

All entries of `assays` should have the same extents for the first two dimensions. However, they can otherwise have any number of other dimensions. Each assay can be of different type.

For `rowdata`, the number of rows must be equal to the extent of the first dimension for each entry in `assays`. Similarly, for `coldata`, the number of rows must be equal to the extent of the second dimension. In both cases, the first column must be called `"name"` and contain a `Vector` of `String`s or `Nothing`s (if no names are available).

`assays` may also be empty.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> assays = OrderedDict{String, AbstractArray}(
          "foobar" => [[1,2] [3,4] [5,6]], 
          "whee" => [[1.2,2.3] [3.4,4.5] [5.6,7.8]]);

julia> rowdata = DataFrame(
          name = [ "X", "Y" ],
          type = ["protein", "transcript"]);

julia> coldata = DataFrame(
          name = [ "a", "b", "c" ],
          treatment = ["normal", "drug1", "drug2"]);

julia> x = SummarizedExperiment(assays, rowdata, coldata)
2x3 SummarizedExperiment
  assays(2): foobar whee
  rownames: X Y
  rowdata(2): name type
  colnames: a b c
  coldata(2): name treatment
  metadata(0):
```
