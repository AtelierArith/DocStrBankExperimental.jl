```
multifilter!(x; samples = nothing, experiments = nothing, colnames = nothing)
```

Return a new `MultiAssayExperiment` that has been filtered to only the specified samples, experiments or column names. This makes a copy of `x` and passes it (and any keyword arguments in `kwargs`) to [`multifilter!`](@ref); see the latter function for more details.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> multifilter(x; samples = ["Patient2", "Patient3"], experiments = "foo")
MultiAssayExperiment object
  experiments(1): foo
  sampledata(2): name disease
  metadata(1): version
```
