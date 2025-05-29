```
pix_write_webp(
    pix::Pix;
    quality::Integer = Int32(80),
    lossless::Bool = true
)::Union{Vector{UInt8}, Nothing}
```

WEBP 画像形式でバイト配列に画像を書き込みます。エラーが発生した場合は `nothing` が返されます。

**引数:**

| T   | 名前       | デフォルト       | 説明                  |
|:--- |:-------- |:----------- |:------------------- |
| R   | pix      |             | ストリームに書き込む画像。       |
| O   | quality  | `Int32(80)` | 画像をエンコードする品質。       |
| O   | lossless | `false`     | ロスレスアルゴリズムを使用するべきか？ |

**制限:**

  * `quality` - `1` から `100` の範囲内でなければなりません。

**詳細:**

ファイルが存在する場合は上書きされます。

lossless が true に設定されている場合、品質は無視されます。
