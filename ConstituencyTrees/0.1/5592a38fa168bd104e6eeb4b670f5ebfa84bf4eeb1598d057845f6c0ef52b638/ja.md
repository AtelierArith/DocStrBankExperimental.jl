```
pprint([io::IO,] tree; indent=2, multiline=true)
```

括弧付き形式で構成解析木を印刷します。

# 引数

  * `io`: 木を書き込むための `IO` ストリーム
  * `tree`: 検索する木

# キーワード

  * `multiline=true`: 文字列表現に改行を含めるかどうか
  * `indent=2`: インデントに使用する空白文字の数（`multiline` が `false` の場合は無視されます）

# 戻り値

  * 構成解析木の括弧付き `String` 表現
