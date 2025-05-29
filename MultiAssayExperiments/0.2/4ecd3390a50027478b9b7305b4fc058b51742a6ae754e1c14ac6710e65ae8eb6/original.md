```
MultiAssayExperiment(experiments)
```

Creates an `MultiAssayExperiment` object from a set of `experiments`. The per-sample column data and sample mapping is automatically created from the union of column names from all `experiments`.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> using SummarizedExperiments

julia> exp = OrderedDict{String, SummarizedExperiment}();

julia> exp["foo"] = SummarizedExperiments.exampleobject(100, 10);

julia> exp["bar"] = SummarizedExperiments.exampleobject(50, 20);

julia> out = MultiAssayExperiment(exp)
MultiAssayExperiment object
  experiments(2): foo bar
  sampledata(1): name
  metadata(0):
```
