```
askAction(
  api_name,
  arguments = Dict(); 
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

はデバイスにアクションを実行するように要求し、結果を `Dict()` で返します。

  * `api_name` と `arguments` はアクションと引数を指定します。

      * `arguments` はオプションで、デフォルトは `Dict()` です。
  * Web API が指示するターゲットデバイスは、2つのオプションのキーワード引数 `target_deviceId` と `target_nickname` を使用して次のように決定されます。

      * 両方のパラメータが省略された場合は `getDefaultDevice()` の結果。
      * いずれかまたは両方のパラメータが存在する場合は `findDevice(deviceId=target_deviceID, nickname=target_nickname)` の結果。
  * `timeoutLimit` <= 0 の場合、即座に `executionId` を返します。
  * そうでない場合は `getExecution(executionId, timeoutLimit)` を呼び出します。
  * `timeoutLimit` はタイムアウトの制限を秒単位で指定し、デフォルトは10秒です。
