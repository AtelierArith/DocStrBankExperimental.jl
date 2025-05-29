```
ZlibCompressorStream(stream::IO)
```

zlib圧縮ストリームを作成します（`kwargs`については`ZlibCompressor`を参照してください）。

!!! warning
    保存された生ポインタのため、このストリームでは`serialize`および`deepcopy`は機能しません。

