```
ZlibDecompressorStream(stream::IO; kwargs...)
```

デフレートデコンプレッションストリームを作成します（`kwargs`については`ZlibDecompressor`を参照してください）。

!!! warning
    `serialize`および`deepcopy`は、保存された生ポインタのため、このストリームでは機能しません。

