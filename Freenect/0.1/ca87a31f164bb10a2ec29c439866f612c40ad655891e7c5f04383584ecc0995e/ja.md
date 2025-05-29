```julia
sync_get_depth(
    index::Integer,
    fmt::Freenect.DepthFormat
) -> Tuple{Matrix{UInt16}, Int64}

```

解像度 `resolution_medium` の同期深度関数で、実行ループが実行されていない場合は開始します。

返される配列は返す前にコピーされ、安全に保存できます。
