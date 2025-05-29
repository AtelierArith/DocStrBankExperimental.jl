```
load_example_data(name; kwargs...) -> InferenceObjects.InferenceData
load_example_data() -> Dict{String,AbstractFileMetadata}
```

Load a local or remote pre-made dataset.

`kwargs` are forwarded to `InferenceObjects.from_netcdf`.

Pass no parameters to get a `Dict` listing all available datasets.

Data files are handled by DataDeps.jl. A file is downloaded only when it is requested and then cached for future use.

# Examples

```jldoctest
julia> keys(load_example_data())
KeySet for a OrderedCollections.OrderedDict{String, ArviZExampleData.AbstractFileMetadata} with 10 entries. Keys:
  "centered_eight"
  "non_centered_eight"
  "radon"
  "rugby"
  "rugby_field"
  "regression1d"
  "regression10d"
  "classification1d"
  "classification10d"
  "glycan_torsion_angles"

julia> load_example_data("centered_eight")
InferenceData with groups:
  > posterior
  > posterior_predictive
  > log_likelihood
  > sample_stats
  > prior
  > prior_predictive
  > observed_data
  > constant_data
```
