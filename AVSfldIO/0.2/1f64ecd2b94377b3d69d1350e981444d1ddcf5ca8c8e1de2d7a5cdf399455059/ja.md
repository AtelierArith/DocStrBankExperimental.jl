```
fld_write(file, data ; kwargs...)
```

AVS形式の`.fld`ファイルにデータを書き込みます。ファイル形式についてはREADMEを参照してください。

引数

  * `file` 通常`.fld`で終わるファイル名
  * `data` 実データ配列

オプション

  * `check::Bool`         ファイルが存在する場合にエラーを報告する; デフォルトは`true`
  * `dir::String`         ファイル名の前に付加するディレクトリ名; デフォルトは`""`
  * `endian::`Symbol``:le`リトルエンディアン（デフォルト）、`:be` ビッグエンディアン
  * `head::Array{String}` ファイルヘッダーのコメント情報
  * `raw::Bool`           生データを`name.raw`に、ヘッダーを`name.fld`に配置する                       ここで`file` = `name.fld`; デフォルトは`false`
