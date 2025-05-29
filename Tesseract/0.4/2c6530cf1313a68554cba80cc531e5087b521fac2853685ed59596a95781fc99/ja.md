```
pix_read_gif(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

バイト配列からGIF画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                  |
|:--- |:---- |:----- |:------------------- |
| R   | data |       | GIF画像を読み込むためのバイト配列。 |
