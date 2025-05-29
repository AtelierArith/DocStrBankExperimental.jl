```
findDevice(;deviceId=nothing, nickname=nothing)
```

は、`deviceID` および/または `nickname` キーが対応するパラメータと一致するデバイスを返します。

  * 両方のパラメータが省略された場合、`getDefaultDevice()` の結果を返します。
  * そのようなデバイスが存在しない場合は `Dict()` を返します。
