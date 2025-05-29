```
pix_read_jpeg(
    data::AbstractArray{UInt8};
    cmap::Bool = false,
    reduction::Integer = Int32(1),
    luminance::Bool = false,
    ignoreErrors::Bool = false
)::Union{Pix, Nothing}
```

バイト配列からJPEG画像を読み込みます。エラーが発生した場合は`nothing`を返します。

**引数:**

| T   | 名前           | デフォルト      | 説明                   |
|:--- |:------------ |:---------- |:-------------------- |
| R   | data         |            | JPEG画像を読み込むためのバイト配列。 |
| O   | cmap         | `false`    | 画像をカラーマップとして読み込む。    |
| O   | reduction    | `Int32(1)` | 解像度を下げた画像を読み込む。      |
| O   | luminance    | `false`    | 画像から輝度データのみを読み込む。    |
| O   | ignoreErrors | `false`    | ファイル内のエラーを無視する。      |

**制限事項:**

  * `cmap` - 画像内のSPPが3または4である必要があるため、すべてのJPEG画像をカラーマップとして読み込むことはできません。
  * `reduction` - 1、2、4、または8でなければなりません。

**詳細:**

`reduction`パラメータは、解像度を下げて画像をより速く読み込むために使用できます。JPEG仕様では、リーダーがビットエラーから回復することを許可しています。`ignoreErrors`をtrueに設定すると、ビットエラーのあるファイルを読み込むことができますが、画像が正しくない可能性があります。
