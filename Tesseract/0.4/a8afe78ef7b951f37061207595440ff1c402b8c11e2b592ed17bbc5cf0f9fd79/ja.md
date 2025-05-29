```
pix_read_jp2k(
    filename::AbstractString;
    reduction::Integer = Int32(1),
    box::Union{PixBox, Nothing} = nothing
)::Union{Pix, Nothing}
```

指定されたファイルからJP2K画像を読み込みます。エラーの場合は`nothing`を返します。

**引数:**

|   T | 名前        | デフォルト      | 説明                   |
| ---:|:--------- |:---------- |:-------------------- |
|   R | filename  |            | 読み込むJP2Kファイルの名前。     |
|   O | reduction | `Int32(1)` | ファイルから画像の縮小版を読み込みます。 |
|   O | box       | `nothing`  | 画像から抽出する領域を指定します。    |

**制限:**

  * `reduction` - 2の倍数でなければなりません。
