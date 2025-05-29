```
GzipDecompressorStream(stream::IO; kwargs...)
```

gzip デコンプレスストリームを作成します（`kwargs`については `GzipDecompressor` を参照してください）。

!!! warning
    保存された生ポインタのため、このストリームでは `serialize` と `deepcopy` は機能しません。

