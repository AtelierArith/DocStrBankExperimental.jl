```
pix_write_webp(
    filename::AbstractString,
    pix::Pix;
    quality::Integer = Int32(80),
    lossless::Bool = true
)::Bool
```

WEBP画像形式でファイルに画像を書き込みます。エラーが発生した場合は`false`が返されます。

**引数:**

| T   | 名前       | デフォルト       | 説明                  |
|:--- |:-------- |:----------- |:------------------- |
| r   | filename |             | 書き込むファイルの名前。        |
| R   | pix      |             | ディスクに書き込む画像。        |
| O   | quality  | `Int32(80)` | 画像をエンコードする品質。       |
| O   | lossless | `false`     | ロスレスアルゴリズムを使用するべきか？ |

**制限:**

  * `quality` - `1`から`100`の範囲内でなければなりません。

**詳細:**

ファイルが存在する場合は上書きされます。

losslessがtrueに設定されている場合、品質は無視されます。
