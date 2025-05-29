```julia
sync_get_video_with_res(
    index::Integer,
    res::Freenect.Resolution,
    fmt::Freenect.VideoFormat
) -> Tuple{Union{Array{UInt8, 3}, Matrix{UInt8}}, Int64}

```

同期ビデオ関数で、実行ループが実行されていない場合は開始します。

返される配列は返す前にコピーされ、安全に保存できます。
