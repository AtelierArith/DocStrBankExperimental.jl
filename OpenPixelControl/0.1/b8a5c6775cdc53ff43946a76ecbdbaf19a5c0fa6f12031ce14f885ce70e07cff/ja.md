```
OpenPixelConnection
```

OPC接続のステータスに必要なすべての情報を含む構造体です。

現時点では、次の1つのフィールドのみが必要です。

  * `connection` は `TCPSocket` です。

# コンストラクタ

  * `OpenPixelConnection()` – `localhost:7890` への接続を生成します。
  * `OpenPixelConnection(port)` – `localhost:port` への接続を生成します。
  * `OpenPixelConnection(host,port)` – `host:port` への接続を生成します。
