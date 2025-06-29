```
pix_read_tiff(
    data::AbstractArray{UInt8};
    page::Integer = Int32(1)
)::Union{Pix, Nothing}
```

バイト配列からTIFF画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト      | 説明                   |
|:--- |:---- |:---------- |:-------------------- |
| R   | data |            | TIFF画像を読み込むためのバイト配列。 |
| O   | page | `Int32(1)` | ファイルから読み込む画像。        |

**制限:**

  * `page` - 0より大きくなければなりません。

**詳細:**

TIFFファイルには複数の画像が含まれることがあります。`page`パラメータを使用して、読み込みたい画像を指定できます。
