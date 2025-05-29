```
DeflateDecompressorStream(stream::IO; kwargs...)
```

デフレートデコンプレッションストリームを作成します（`kwargs`については`DeflateDecompressor`を参照してください）。

!!! warning
    保存された生ポインタのため、このストリームでは`serialize`および`deepcopy`は機能しません。

