```
MultiAssayExperiments.exampleobject()
```

Create an example `MultiAssayExperiment` object.  This is to be used to improve the succinctness of examples and tests.

# Examples

```jldoctest
julia> using MultiAssayExperiments 

julia> x = MultiAssayExperiments.exampleobject()
MultiAssayExperiment object
  experiments(2): foo bar
  sampledata(2): name disease
  metadata(1): version
```
