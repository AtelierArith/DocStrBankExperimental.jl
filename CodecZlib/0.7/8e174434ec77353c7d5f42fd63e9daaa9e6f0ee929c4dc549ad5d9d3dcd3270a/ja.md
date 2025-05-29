```
GzipCompressorStream(stream::IO; kwargs...)
```

gzip 圧縮ストリームを作成します（`kwargs`については `GzipCompressor` を参照してください）。

!!! warning
    保存された生ポインタのため、このストリームでは `serialize` と `deepcopy` は機能しません。

