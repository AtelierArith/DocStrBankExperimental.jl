```
load_pubchem_json(fname::AbstractString, ::Type{T} = Float32) -> System{T}
```

PubChemのJSONファイルを読み込みます。

!!! note
    コンフォーマーはフレームとして保存されます。

