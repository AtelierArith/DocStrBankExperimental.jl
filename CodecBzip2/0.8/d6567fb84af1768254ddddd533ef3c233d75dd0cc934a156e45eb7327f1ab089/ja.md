```
Bzip2CompressorStream(stream::IO; kwargs...)
```

bzip2 圧縮ストリームを作成します（`kwargs`については `Bzip2Compressor` を参照してください）。

!!! warning
    保存された生ポインタのため、このストリームでは `serialize` と `deepcopy` は機能しません。

