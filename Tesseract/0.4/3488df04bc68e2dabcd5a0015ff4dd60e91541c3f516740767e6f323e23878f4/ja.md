```
pix_read_spix(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

バイト配列からSPIX画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

| T   | 名前   | デフォルト | 説明                   |
|:--- |:---- |:----- |:-------------------- |
| R   | data |       | SPIX画像を読み込むためのバイト配列。 |
