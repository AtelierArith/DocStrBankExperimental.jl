```
update!(obj, data[; provider, kwargs...])
```

ハッシュコンテキストまたはHMACオブジェクト`obj`に`data`をフィードします。

引数`data`は、`AbstractVector{UInt8}`、`AbstractString`、`IO`、またはバイトのベクターに収集できる他の任意の型であることができます。

`IO`型の`data`を読み取る際には、オプションのキーワード引数`buffersize`でバッファサイズを設定できます。
