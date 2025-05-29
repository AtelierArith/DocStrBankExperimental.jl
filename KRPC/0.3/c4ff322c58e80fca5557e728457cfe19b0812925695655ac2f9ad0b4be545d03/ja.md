```
kerbal(c::KRPCConnection, call::Request{S, P, R}) where {S, P, R}
```

接続 `c` を使用してサーバーに単一のメッセージ `call` を送信します。 有効なリクエストについては、KRPC.Interface.[service] モジュールで生成された呼び出しスタブを参照してください。

# 例

```
active_vessel = kerbal(conn, KRPC.Interface.SpaceCenter.get_ActiveVessel())
```
