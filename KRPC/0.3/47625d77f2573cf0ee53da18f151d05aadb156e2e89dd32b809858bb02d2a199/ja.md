```
kerbal(c::KRPCConnection, calls::T) where {K, T<:Tuple{Vararg{RT where {S, P, R, RT<:Request{S, P, R}}, K}}}
```

接続 `c` を使用して、サーバーに複数のメッセージ `calls` を送信します。 有効なリクエストについては、KRPC.Interface.[service] モジュールで生成された呼び出しスタブを参照してください。

# 例

```
active_vessel, gamemode = kerbal(conn, (KRPC.Interface.SpaceCenter.get_ActiveVessel(), KRPC.Interface.SpaceCenter.get_GameMode()))
```
