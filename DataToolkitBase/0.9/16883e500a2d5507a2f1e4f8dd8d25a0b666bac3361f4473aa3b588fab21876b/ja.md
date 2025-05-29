```
dataset([collection::DataCollection], identstr::AbstractString, [parameters::Dict{String, Any}])
dataset([collection::DataCollection], identstr::AbstractString, [parameters::Pair{String, Any}...])
```

`identstr` で識別されるデータセットを返します。オプションで、データセットが見つかるべき `collection` と適用される `parameters` を指定できます。
