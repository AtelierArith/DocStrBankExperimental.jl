```
exportqrcode( message::AbstractString
            , path = "qrcode.png"
            , eclevel = Medium()
            ; targetsize = 5
            , compact = false )
```

エンコードされた `message` をおおよそ `targetsize` cm のサイズで `PNG` ファイルとして作成します。`compact` が `false` の場合、QR コードの周りに余白が追加されます。

誤り訂正レベル `eclevel` は、次の4つの値から選択できます: `Low()` (7% の欠損データを復元可能)、`Medium()` (15%)、`Quartile()` (25%) または `High()` (30%)。より高いレベルは、より密な QR コードを生成します。
