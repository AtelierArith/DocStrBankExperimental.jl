```
dropunused(x; kwargs...)
```

Return a new `MultiAssayExperiment` where unused samples, experiments or column names are removed. This makes a copy of `x` and passes it (and any keyword arguments in `kwargs`) to [`dropunused!`](@ref); see the latter function for more details.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> y = filtersamplemap(x; experiments = "bar"); # Only keeping experiment 'bar'

julia> dropunused(y) # We see that 'foo' is dropped
MultiAssayExperiment object
  experiments(1): bar
  sampledata(2): name disease
  metadata(1): version
```
