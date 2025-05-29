```
function remove_urls_from_index(index_path::AbstractString, prefix_urls=Vector{<:AbstractString})
```

`prefix_urls` で始まる URL に対応するチャンクとソースを削除します。
