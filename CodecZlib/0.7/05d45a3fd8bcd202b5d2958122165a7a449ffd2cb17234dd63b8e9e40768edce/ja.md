```
DeflateCompressorStream(stream::IO; kwargs...)
```

deflate圧縮ストリームを作成します（`kwargs`については`DeflateCompressor`を参照してください）。

!!! warning
    `serialize`および`deepcopy`は、保存された生ポインタのため、このストリームでは機能しません。

