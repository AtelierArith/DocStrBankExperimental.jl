```
getbridgeinfo(bridge[, category::String])
```

ブリッジから情報を取得します。カテゴリは次のいずれかです：

  * "lights" リソースはすべてのライトリソースを含みます
  * "groups" リソースはすべてのグループを含みます
  * "config" リソースはすべての設定項目を含みます
  * "schedules" はすべてのスケジュールを含みます
  * "scenes" はすべてのシーンを含みます
  * "sensors" はすべてのセンサーを含みます
  * "rules" はすべてのルールを含みます

デフォルトは "config" です。
