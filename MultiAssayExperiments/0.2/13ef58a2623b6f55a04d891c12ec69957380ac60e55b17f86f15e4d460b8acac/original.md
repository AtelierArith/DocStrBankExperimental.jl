```
dropunused!(x; samples = true, experiments = true, colnames = true, mapping = true)
```

Drop unused samples, experiments and/or column names from the `MultiAssayExperiment` `x`. A reference to the modified `x` is returned.

If `samples = true`, `sampledata(x)` is filtered to only retain samples that are present in the sample mapping.

If `experiments = true`, `experiments(x)` is filtered to only retain experiments that are present in the sample mapping.

If `colnames = true`, each entry of `experiments(x)` is filtered to only retain column names that are present in the sample mapping for that experiment.

If `mapping = true`, the sample mapping is filtered to remove rows that contain samples, experiments or column names that do not exist in `x`.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> filtersamplemap!(x; experiments = "bar"); # Only keeping experiment 'bar'

julia> dropunused!(x) # We see that 'foo' is dropped
MultiAssayExperiment object
  experiments(1): bar
  sampledata(2): name disease
  metadata(1): version
```
