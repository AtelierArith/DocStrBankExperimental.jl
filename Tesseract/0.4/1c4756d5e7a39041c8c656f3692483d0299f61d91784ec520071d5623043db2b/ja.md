```
pix_write_jpeg(
    stream::IO,
    pix::Pix;
    quality::Integer = Int32(75),
    progressive::Bool = false
)::Bool
```

IOストリームにJPEG画像形式で画像を書き込みます。エラーが発生した場合は`false`が返されます。

**引数:**

| T   | 名前          | デフォルト       | 説明                             |
|:--- |:----------- |:----------- |:------------------------------ |
| R   | stream      |             | 画像を書き込むストリーム。                  |
| R   | pix         |             | ストリームに書き込む画像。                  |
| O   | quality     | `Int32(75)` | 画像をエンコードする品質。                  |
| O   | progressive | `false`     | プログレッシブエンコーディングアルゴリズムを使用するべきか？ |

**制限:**

  * `quality` - 1から100の範囲内でなければなりません。
