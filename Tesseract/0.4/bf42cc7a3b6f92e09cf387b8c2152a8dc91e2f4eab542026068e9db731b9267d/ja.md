```
pix_read(
    filename::AbstractString;
    jpgLuminance::Bool = false,
    jpgFailOnBadData::Bool = false
)::Union{Pix, Nothing}
```

ディスクから未指定のタイプの画像を読み込みます。ファイルを読み込めなかった場合は `nothing` を返します。

**引数:**

| T   | 名前               | デフォルト   | 説明                          |
|:--- |:---------------- |:------- |:--------------------------- |
| R   | filename         |         | 読み込む画像のファイル名。               |
| O   | jpgLuminance     | `false` | 画像がJPEGの場合、輝度データのみを読み込むべきか？ |
| O   | jpgFailOnBadData | `false` | 画像がJPEGの場合、ビットエラーを無視するべきか？  |

**詳細:**

2つのオプションのパラメータは、画像がJPEGでない場合は明らかに無視されます。
