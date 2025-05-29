```
export_cff(e::Entry, destination::String="CITATION.cff", version::String="1.2.0", add_preferred::Bool=true) -> Dict{String, Any}
```

`Entry`をCFFファイルにエクスポートします（デフォルトは`CITATION.cff`です）。
