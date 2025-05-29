```
QRInfo
```

QRコードの情報を格納するための構造体です。

## フィールド

  * `version::Int`: QRコードのバージョン
  * `eclevel::Int`: QRコードの誤り訂正レベル
  * `mask::Int`: QRコードのマスク
  * `mode::Int`: QRコードのモード
  * `message::String`: デコードされたメッセージ
