```
download(rf::RemoteFile;
         quiet::Bool=false,
         verbose::Bool=false,
         force::Bool=false,
         retries::Int=0)
```

`rf`をダウンロードします。

  * `quiet`: メッセージを表示しません。
  * `verbose`: すべてのメッセージを表示します。
  * `force`: ダウンロードを強制し、既存のファイルを上書きします。
  * `force_update`: 既存のファイルが等しい場合でも上書きします。
  * `retries`: `retries != 0`の場合、`rf`のリトライ回数を上書きします。
