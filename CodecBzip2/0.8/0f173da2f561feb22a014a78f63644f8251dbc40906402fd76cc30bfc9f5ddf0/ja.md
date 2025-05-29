```
Bzip2DecompressorStream(stream::IO; kwargs...)
```

bzip2 デコンプレッションストリームを作成します（`kwargs`については `Bzip2Decompressor` を参照してください）。

!!! warning
    保存された生ポインタのため、このストリームでは `serialize` と `deepcopy` は機能しません。

