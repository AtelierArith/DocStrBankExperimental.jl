```
pix_read_bmp(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

バイト配列からBMP画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | data |       | BMP画像を読み込むためのバイト配列。 |
