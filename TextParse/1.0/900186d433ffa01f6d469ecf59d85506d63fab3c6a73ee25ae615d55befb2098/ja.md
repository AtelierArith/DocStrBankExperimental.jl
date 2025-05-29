```
csvread(file::Union{String,IO}, delim=','; <arguments>...)
```

`file`からCSVを読み込みます。2つの要素からなるタプルを返します：

1. 各列が`Vector`または`StringArray`のタプル
2. `header_exists=true`の場合は列名、そうでない場合は空の配列

# 引数：

  * `file`: IOオブジェクトまたはファイル名の文字列
  * `delim`: 区切り文字
  * `spacedelim`: (Bool) スペース区切りのファイルを解析します。trueの場合、`delim`は無効になります。
  * `quotechar`: 文字列を引用するために使用される文字、デフォルトは`"`
  * `escapechar`: 文字列内のquotecharをエスケープするために使用される文字。（quotecharと同じである可能性があります）
  * `commentchar`: commentcharで始まる行を無視します
  * `row_estimate`: ファイル内の行数の推定値。デフォルトは`0`で、この場合は推定を試みます。
  * `skiplines_begin`: ファイルの先頭で指定された行数をスキップします
  * `header_exists`: CSVファイルにヘッダーが含まれているかどうかを指定するブール値
  * `nastrings`: NAと見なされる文字列。デフォルトは`TextParse.NA_STRINGS`
  * `colnames`: 手動で指定された列名。ベクトルまたは整数インデックス（列）から文字列列名への辞書である可能性があります。
  * `colparsers`: 指定された列に使用するパーサー。これは、列名/列インデックス（Int）から「パーサー」へのベクトルまたは辞書である可能性があります。最も単純なパーサーはIntやFloat64のような型です。また、`dateformat"..."`であることもできます。カスタム解析動作をプラグインしたい場合は、[CustomParser](@ref)を参照してください。特定の列のパーサーとして`nothing`を渡すと、その列はスキップされます。
  * `type_detect_rows`: 初期`colparsers`を推測するために使用する行数、デフォルトは20です。
