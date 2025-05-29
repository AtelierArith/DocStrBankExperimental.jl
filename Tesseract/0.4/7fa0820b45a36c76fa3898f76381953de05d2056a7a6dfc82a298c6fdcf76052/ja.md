```
pix_write_tiff(
    filename::AbstractString,
    pix::Pix;
    compression::IFF = IFF_TIFF,
    append::Bool = false
)::Bool
```

TIFF画像形式でファイルに画像を書き込みます。エラーが発生した場合は`false`を返します。

**引数:**

| T   | 名前          | デフォルト      | 説明                    |
|:--- |:----------- |:---------- |:--------------------- |
| R   | filename    |            | 書き込むか作成するファイルの名前。     |
| R   | pix         |            | ディスクに書き込む画像。          |
| O   | compression | `IFF_TIFF` | 画像に使用する圧縮形式。          |
| O   | append      | `false`    | 画像を上書きするか、ファイルに追加するか。 |

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

デフォルトの圧縮は無圧縮です。

TIFFファイルは複数の画像を含むことができます。ファイルが存在しない場合は作成されます。ファイルが存在し、appendが`false`の場合、ファイルは上書きされます。appendが`true`の場合、画像はファイルに追加されます。
