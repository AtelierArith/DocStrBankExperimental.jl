```
head = fld_header(file::String ; dir::String="", chat=false)
```

AVS形式の`.fld`ファイルからヘッダーデータを読み取り、その後ファイルを閉じます。

入力

  * `file::String` ファイル名、通常は`.fld`で終わります。

オプション

  * `dir::String` このディレクトリでファイル名を前置きします; デフォルトは""
  * `chat::Bool` 詳細表示しますか？ デフォルト: `false`

出力

  * `head::String` ヘッダー情報の配列
