```
qrcode(message::AbstractString, eclevel = Medium(); compact = false)
```

エンコードされた `message` を持つ `BitArray{2}` を作成します。黒い部分には `true` (`1`) を、白い部分には `false` (`0`) を使用します。`compact` が `false` の場合、QR コードの周りに余白が追加されます。

エラー訂正レベル `eclevel` は、4 つの値から選択できます: `Low()` (欠損データの 7% を復元可能)、`Medium()` (15%)、`Quartile()` (25%) または `High()` (30%)。より高いレベルは、より密な QR コードを生成します。
