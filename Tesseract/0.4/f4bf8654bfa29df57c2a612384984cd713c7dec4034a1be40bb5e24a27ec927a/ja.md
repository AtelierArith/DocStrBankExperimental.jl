```
pix_read_pnm(
    filename::AbstractString
)::Union{Pix, Nothing}
```

指定されたファイルからPNG画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

| T   | 名前       | デフォルト | 説明              |
|:--- |:-------- |:----- |:--------------- |
| R   | filename |       | 読み込むPNMファイルの名前。 |
