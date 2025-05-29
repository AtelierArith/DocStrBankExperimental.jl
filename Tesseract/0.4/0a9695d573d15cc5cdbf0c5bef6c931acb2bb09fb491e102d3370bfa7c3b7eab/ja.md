```
pix_read_jp2k(
    stream::IO;
    reduction::Integer = Int32(1),
    box::Union{PixBox, Nothing} = nothing
)::Union{Pix, Nothing}
```

指定されたストリームからJP2K画像を読み込みます。エラーが発生した場合は`nothing`を返します。

**引数:**

| T   | 名前        | デフォルト      | 説明                       |
|:--- |:--------- |:---------- |:------------------------ |
| R   | stream    |            | JP2Kファイルを読み込むためのIOストリーム。 |
| O   | reduction | `Int32(1)` | ファイルから画像の縮小版を読み込みます。     |
| O   | box       | `nothing`  | 画像から抽出する領域を指定します。        |

**制限:**

  * `reduction` - 2の倍数でなければなりません。

**詳細:**

この実装は、FILEポインタを渡すときにLeptonicaが提供するAPIを反映しています。これは、ストリームの残りがJP2K画像を含むことを前提としています。
