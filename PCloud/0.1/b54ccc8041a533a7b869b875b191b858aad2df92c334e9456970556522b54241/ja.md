```
getip(client::PCloudClient; kwargs...)
```

APIに接続するユーザーが接続しているリモートデバイスのIPアドレスを取得します。

Source: https://docs.pcloud.com/methods/general/getip.html

# 出力

`ip` - APIに接続しているユーザーのリモートアドレスを返します。

また、`country` - リモートアドレスに基づいて定義される国の小文字の2文字コードを返します。国を特定できなかった場合、このフィールドは`false`になります。

# 出力例

```
{
  "result": 0,
  "ip": "127.0.0.1",
  "country": "gb"
  ]
}
```
