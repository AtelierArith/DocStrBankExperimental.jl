```
getDevices(accessToken)
```

は `accessToken` に関連付けられたデバイスリストを取得しようとします。

成功した場合、 

  * `Array{Dict}` 型のデバイスリストを返します。
  * `accessToken` をローカル変数 `currentAccessToken` に割り当てます。
  * 非空のデバイスリストが見つかった場合、`currentDevices` と `defaultDevice` を更新します。具体的には、
  * 見つかったデバイスリストをローカル変数 `currentDevices` に割り当てます。
  * `currentDevices` が空でない場合、`currentDevices` の最初の要素をローカル変数 `defaultDevice` に割り当てます。
