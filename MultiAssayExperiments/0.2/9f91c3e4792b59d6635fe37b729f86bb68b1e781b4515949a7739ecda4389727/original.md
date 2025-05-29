```
experiment(x[, i]; sampledata = false)
```

Extract the specified `SummarizedExperiment` from a `MultiAssayExperiment` `x`. `i` may be a positive integer no greater than the number of experiments in `x`, or a string specifying the name of the desired experiment. If `i` is not specified, it defaults to the first experiment in `x`.

If `sampledata = true`, we attempt to add the sample data of `x` to the `coldata` of the returned `SummarizedExperiment`. This is done by subsetting `sampledata(x)` based on sample mapping to the columns of the returned `SummarizedExperiment` - see [`expandsampledata`](@ref) for more details. If there are columns in the `sampledata(x)` and the `coldata` of the `SummarizedExperiment` with the same name but different values, the former are omitted with a warning.

Note that, if `sampledata = true`, the returned `SummarizedExperiment` will be a copy of the relevant experiment in `x`. If `false`, the returned object will be a reference.

# Examples

```jldoctest
julia> using MultiAssayExperiments;

julia> x = MultiAssayExperiments.exampleobject();

julia> experiment(x)
100x10 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene99 Gene100
  rowdata(2): name Type
  colnames: foo1 foo2 ... foo9 foo10
  coldata(3): name Treatment Response
  metadata(1): version

julia> experiment(x, 1); # same result

julia> experiment(x, "foo");

julia> experiment(x, "foo", sampledata = true) # add sample data
100x10 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene99 Gene100
  rowdata(2): name Type
  colnames: foo1 foo2 ... foo9 foo10
  coldata(4): name Treatment Response disease
  metadata(1): version
```
