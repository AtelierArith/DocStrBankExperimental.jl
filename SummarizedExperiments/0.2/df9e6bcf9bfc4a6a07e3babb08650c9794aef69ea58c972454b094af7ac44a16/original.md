```
SummarizedExperiment(assays)
```

Create an instance of a `SummarizedExperiment` with the supplied assays.

All entries of `assays` should have the same extents for the first two dimensions. However, they can otherwise have any number of other dimensions. Each assay can be of different type. `assays` should contain at least one assay matrix.

For the `coldata` and `rowdata`, an empty `DataFrame` is created with a `"name"` column containing all `nothing`s.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> assays = OrderedDict{String, AbstractArray}(
          "foobar" => [[1,2] [3,4] [5,6]], 
          "whee" => [[1.2,2.3] [3.4,4.5] [5.6,7.8]]);

julia> x = SummarizedExperiment(assays)
2x3 SummarizedExperiment
  assays(2): foobar whee
  rownames:
  rowdata(1): name
  colnames:
  coldata(1): name
  metadata(0):
```
