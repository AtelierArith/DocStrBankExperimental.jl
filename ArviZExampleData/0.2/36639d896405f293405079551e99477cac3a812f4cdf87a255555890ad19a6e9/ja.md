```
load_example_data(name; kwargs...) -> InferenceObjects.InferenceData
load_example_data() -> Dict{String,AbstractFileMetadata}
```

ローカルまたはリモートの事前作成されたデータセットをロードします。

`kwargs` は `InferenceObjects.from_netcdf` に転送されます。

パラメータを指定せずに呼び出すと、利用可能なデータセットのリストを含む `Dict` が得られます。

データファイルは DataDeps.jl によって処理されます。ファイルは要求されたときにのみダウンロードされ、その後将来の使用のためにキャッシュされます。

# 例

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
