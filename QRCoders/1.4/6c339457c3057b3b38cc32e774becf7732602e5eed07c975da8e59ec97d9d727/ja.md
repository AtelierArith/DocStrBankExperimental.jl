```
QRCode
```

QRコードを表す型です。

# フィールド

  * `version::Int`: QRコードのバージョン
  * `mode::Mode`: QRコードのエンコーディングモード
  * `eclevel::ErrCorrLevel`: QRコードの誤り訂正レベル
  * `mask::Int`: QRコードのマスクパターン
  * `message::String`: エンコードされるメッセージ
  * `border::Int`: 白い境界の幅
