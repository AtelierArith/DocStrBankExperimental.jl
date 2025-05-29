```
masterTrigger(rpc::RedPitayaCluster, val::Bool)
```

クラスタのマスタートリガーを `val` に設定します。

`val` が true の場合、これは `master(rpc)` で返された RedPitaya に対して関数を呼び出すのと同じです。`val` が false の場合、マスタートリガーが無効にされる前に、クラスタ内のすべての RedPitaya に対して keepAliveReset が true に設定されます。その後、keepAliveReset は再び false に設定されます。

関連情報として [`master`](@ref)、[`keepAliveReset!`](@ref) を参照してください。
