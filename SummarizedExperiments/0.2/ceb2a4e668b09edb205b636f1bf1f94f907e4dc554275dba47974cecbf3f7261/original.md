```
exampleobject(nrow, ncol)
```

Create an example `SummarizedExperiment` object with the specified number of rows and columns. This is to be used to improve the succinctness of examples and tests.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10)
20x10 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene19 Gene20
  rowdata(2): name Type
  colnames: Patient1 Patient2 ... Patient9 Patient10
  coldata(3): name Treatment Response
  metadata(1): version
```
