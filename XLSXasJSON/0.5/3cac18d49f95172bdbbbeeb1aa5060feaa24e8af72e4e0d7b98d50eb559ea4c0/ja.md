```
JSONWorkbook(file::AbstractString; start_line = 1)
```

各シートの`start_line`はデータ構造のJSONPointerとして考慮されます。そして各シートは`Array{PointerDict, 1}`にパースされます。

# コンストラクタ

```julia
JSONWorkbook("Example.xlsx")
```

# 引数

引数はWorkbook内のすべてのワークシートに適用されます。

  * `row_oriented` : 'true'（デフォルト）の場合、'1:1'で列名を探します。`false`の場合、'A:A'で列名を探します。
  * `start_line` : 列名の位置の開始インデックス。
  * `squeeze` : ワークシートのすべての行を単一の行に圧縮します。
  * `delim` : 単一のセルを配列に変換するための区切り文字の文字列または正規表現。
