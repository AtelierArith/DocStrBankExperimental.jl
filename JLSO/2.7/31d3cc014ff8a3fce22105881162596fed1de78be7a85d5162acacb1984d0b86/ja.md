```
JLSOFile(data; format=:julia_serialize, compression=:gzip, kwargs...)
```

.jlsoファイルを書くために必要な情報を保存します。

# 引数

  * `data` - ファイルに保存するオブジェクト。

# キーワード

  * `image=""` - ファイルを生成するために使用されたDockerイメージのURI
  * `julia=1.11.5` - ファイルを書くために使用されたJuliaのバージョン
  * `version=v"4"` - ファイルスキーマのバージョン
  * `format=:julia_serialize` - 個々のオブジェクトをシリアライズするために使用するフォーマット。長期的なオブジェクトストレージには`:bson`が推奨されますが、`:julia_serialize`はアドホックシリアライズにはより速い選択肢です。
  * `compression=:gzip`、オブジェクトに適用する圧縮の形式。圧縮しない場合は`:none`を使用します。最速のgzip圧縮には`:gzip_fastest`、最もコンパクト（ただし最も遅い）には`:gzip_smallest`、一般的に良い妥協には`:gzip`を使用します。ディスクIOにかかる時間のため、通常`:none`は何らかの圧縮を使用するよりも速くはありません。
