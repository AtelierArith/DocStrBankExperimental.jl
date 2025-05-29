```
pix_write_tiff(
    stream::IO,
    pix::Pix;
    compression::IFF = IFF_TIFF
)::Bool
```

TIFF画像形式でIOストリームに画像を書き込みます。エラーが発生した場合は`false`を返します。

**引数:**

| T   | 名前          | デフォルト      | 説明            |
|:--- |:----------- |:---------- |:------------- |
| R   | stream      |            | 画像を書き込むストリーム。 |
| R   | pix         |            | ディスクに書き込む画像。  |
| O   | compression | `IFF_TIFF` | 画像に使用する圧縮形式。  |

**制限:**

  * `compression` - 次の圧縮形式のいずれかでなければなりません:

      * `IFF_TIFF` - すべての画像をサポートします。
      * `IFF_TIFF_RLE` - 白黒1bpp画像が必要です。
      * `IFF_TIFF_PACKBITS` - 白黒1bpp画像が必要です。
      * `IFF_TIFF_G3` - 白黒1bpp画像が必要です。
      * `IFF_TIFF_G4` - 白黒1bpp画像が必要です。
      * `IFF_TIFF_LZW` - すべての画像をサポートします。
      * `IFF_TIFF_ZIP` - すべての画像をサポートします。
      * `IFF_TIFF_JPEG` - すべての画像をサポートします。

**詳細:**

デフォルトの圧縮は圧縮なしです。
