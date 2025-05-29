```
rmproc(vm[; session=AzSession(;lazy=true), verbose=0, nretry=10])
```

`addproc` メソッドを使用して作成された VM を削除します。

# パラメータ

  * `session=AzSession(;lazy=true)` OAuth2 認証のための Azure セッション
  * `verbose=0` HTTP.jl メソッドに渡される冗長性フラグ
  * `nretry=10` 再試行可能な REST 呼び出しの最大再試行回数
  * `show_quota=false` 様々な操作の後に "x-ms-rate-remaining-resource" レスポンスヘッダーを表示します。 Azure のクォータをデバッグ/理解するのに役立ちます。
