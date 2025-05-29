```
heartbeat_ping(c::Client) -> Nullable{Period}
```

[`Client`](@ref)のゲートウェイへのピング時間を取得します。クライアントが接続されていない場合、またはハートビートが送信されていない/確認されていない場合は、`nothing`が返されます。
