```
pix_read_spix(
    stream::IO
)::Union{Pix, Nothing}
```

指定されたストリームからSPIX画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

| T   | 名前     | デフォルト | 説明                       |
|:--- |:------ |:----- |:------------------------ |
| R   | stream |       | SPIXファイルを読み込むためのIOストリーム。 |

**詳細:**

この実装は、FILEポインタを渡すときにLeptonicaが提供するAPIを反映しています。ストリームの残りがSPIX画像を含むことを前提としています。
