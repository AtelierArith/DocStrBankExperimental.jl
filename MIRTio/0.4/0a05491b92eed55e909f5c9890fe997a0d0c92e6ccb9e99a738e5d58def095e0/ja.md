```
ht = header_read(fid::IOStream, hd::Matrix{Any} ; seek0::Bool)
```

スキャンファイルからヘッダーを読み取ります

入力

  * `fid::IOStream` は open(file, "r" ) から
  * `hd` ヘッダー定義配列 (N × 3)、例: `header_example()` から

オプション

  * `seek0::Bool` 最初にファイルの `0` 位置にシークしますか？ デフォルトは `true`

出力

  * `ht::NamedTuple` ヘッダー値を含み、ht.key でアクセスされます
