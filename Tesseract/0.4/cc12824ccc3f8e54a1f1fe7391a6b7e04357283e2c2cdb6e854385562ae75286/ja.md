```
pix_write_tiff(
    pix::Pix;
    compression::IFF = IFF_TIFF
)::Union{Vector{UInt8}, Nothing}
```

TIFF画像形式でバイト配列に画像を書き込みます。エラーが発生した場合は`nothing`を返します。

**引数:**

| T   | 名前          | デフォルト      | 説明            |
|:--- |:----------- |:---------- |:------------- |
| R   | pix         |            | バイト配列に書き込む画像。 |
| O   | compression | `IFF_TIFF` | 画像に使用する圧縮形式。  |

**制限:**

  * `compression` - 次の圧縮形式のいずれかでなければなりません:

      * `IFF_TIFF` - すべての画像をサポート。
      * `IFF_TIFF_RLE` - 白黒1bpp画像が必要。
      * `IFF_TIFF_PACKBITS` - 白黒1bpp画像が必要。
      * `IFF_TIFF_G3` - 白黒1bpp画像が必要。
      * `IFF_TIFF_G4` - 白黒1bpp画像が必要。
      * `IFF_TIFF_LZW` - すべての画像をサポート。
      * `IFF_TIFF_ZIP` - すべての画像をサポート。
      * `IFF_TIFF_JPEG` - すべての画像をサポート。

**詳細:**

デフォルトの圧縮は圧縮なしです。
