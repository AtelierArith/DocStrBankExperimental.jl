```
JSONWorksheet
```

ワークシートから各行のために 'Array{OrderedDict, 1}' を構築します

# コンストラクタ

```julia
JSONWorksheet("Example.xlsx", "Sheet1")
JSONWorksheet("Example.xlsx", 1)

```

# 引数

  * `row_oriented` : 'true'（デフォルト）の場合、'1:1' で列名を探します。`false` の場合、'A:A' で列名を探します。
  * `start_line` : 列名の位置の開始インデックス。
  * `squeeze` : ワークシートのすべての行を単一の行に圧縮します。
  * `delim` : 単一のセルを配列に変換するための区切り文字の文字列または正規表現。
