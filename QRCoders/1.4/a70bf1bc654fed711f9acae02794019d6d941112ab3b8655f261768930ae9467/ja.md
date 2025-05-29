```
exportqrcode( message::AbstractString
            , path::AbstractString = "qrcode.png"
            ; eclevel::ErrCorrLevel = Medium()
            , version::Int = 0
            , mode::Mode = nothing
            , width::int = 4
            , pixels::Int = 160)
```

エンコードされた `message` を持つ画像を、約 `pixels x pixels` のサイズで作成します。

エラー訂正レベル `eclevel` は、4つの値から選択できます： `Low()`（7%の欠損データを復元可能）、`Medium()`（15%）、`Quartile()`（25%）または `High()`（30%）。高いレベルは、より密なQRコードを生成します。

QRコードのバージョンは1から40の中から選択できます。割り当てられたバージョンがメッセージを含むには小さすぎる場合、最初に利用可能なバージョンが使用されます。

エンコーディングモード `mode` は、4つの値から選択できます： `Numeric()`、`Alphanumeric()`、`Byte()`、`Kanji()` または `UTF8()`。割り当てられた `mode` が `nothing` であるか、メッセージを含むことに失敗した場合、モードは自動的に選択されます。

マスクパターン `mask` は0から7の中から選択できます。割り当てられた `mask` が `nothing` の場合、マスクパターンはペナルティルールによって選択されます。
