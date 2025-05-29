```
dataset([collection::DataCollection], identstr::AbstractString, [parameters::Dict{String, Any}])
dataset([collection::DataCollection], identstr::AbstractString, [parameters::Pair{String, Any}...])
```

Return the data set identified by `identstr`, optionally specifying the `collection` the data set should be found in and any `parameters` that apply.
