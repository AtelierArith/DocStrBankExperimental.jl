```
geqdsk_to_imas!(
    eqdsk_file::String,
    dd::IMAS.dd;
    set_time::Union{Nothing, Float64}=nothing,
    time_index::Int=1,
)
```

EFITスタイルのgEQDSKファイルからIMAS DD構造体への平衡再構築を転送します。
