```
getapiserver(client::PCloudClient; kwargs...)
```

このメソッドは、リクエストを行ったクライアントに最も近いAPIサーバーを返します。最大の速度向上はアップロードメソッドで得られます。クライアントはフォールバックロジックを持つべきです。APIサーバーへのリクエストがapi.pcloud.comとは異なる場合に失敗した場合（ネットワークエラー）、クライアントはapi.pcloud.comを使用するようにフォールバックする必要があります。

Source: https://docs.pcloud.com/methods/general/getapiserver.html

# 出力

binapi - pCloudのバイナリプロトコルを介して接続をサポートするAPIサーバーの配列

api - HTTP/HTTPSプロトコルを介して接続をサポートするAPIサーバーの配列

# 出力例

```
{
  "result": 0,
  "binapi": [
    "binapi-ams1.pcloud.com"
  ],
  "api": [
    "api-ams1.pcloud.com"
  ]
}
```
