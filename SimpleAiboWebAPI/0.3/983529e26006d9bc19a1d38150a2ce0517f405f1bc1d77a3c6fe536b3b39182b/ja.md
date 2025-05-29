```
askActionSimple(
  api_name,
  arguments,
  target_deviceId,
  timeoutLimit = 10)
```

はデバイスにアクションを実行するように要求し、結果を `Dict()` で返します。

  * `api_name` と `arguments` はアクションと引数を指定します。
  * `target_deviceId` はターゲットデバイスの deviceId を指定します。
  * `timeoutLimit` <= 0 の場合、即座に `executionId` を返します。
  * そうでない場合、`getExecution(executionId, timeoutLimit)` を呼び出します。
  * `timeoutLimit` はタイムアウトの制限を秒単位で指定し、デフォルトは 10（秒）です。
