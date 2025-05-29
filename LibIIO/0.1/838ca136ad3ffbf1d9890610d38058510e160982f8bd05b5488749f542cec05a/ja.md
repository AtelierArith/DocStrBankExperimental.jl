```
find_channel(d::AbstractDeviceOrTrigger, name_or_id, is_output = false)
```

名前またはIDでIIOチャネルを見つけます。

# パラメータ

  * `d` : デバイスインスタンス
  * `name_or_id` : 見つけるチャネルの名前またはID
  * `is_output` : 出力チャネルを検索するにはtrueに設定

# 戻り値

  * `Channel`としてのIIOチャネル
