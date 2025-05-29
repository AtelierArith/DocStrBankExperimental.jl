```
head, is_external_file, fid = fld_open(file ; dir::String="", chat=false)
```

AVS形式の`.fld`ファイルからヘッダーデータを読み取ります。さらに読み取るためにファイルを開いたままにします。

入力

  * `file::String` ファイル名、通常は`.fld`で終わります

オプション

  * `dir::String` このディレクトリでファイル名を前置きします; デフォルトは""
  * `chat::Bool` 詳細表示しますか？ デフォルト: `false`

出力

  * `head::String` ヘッダー情報の配列
  * `is_external_file::Bool` AVS外部形式の場合はtrue
  * `fid::IOstream`
