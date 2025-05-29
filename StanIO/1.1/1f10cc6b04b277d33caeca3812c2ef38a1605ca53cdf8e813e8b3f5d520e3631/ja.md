```julia
parse_header(header)

```

与えられたカンマ区切りのStan出力名のリスト（CSVファイルのヘッダー行からのもの）を解析し、`Variable`オブジェクトの（順序付き）辞書に変換します。

## パラメータ

header::Vector{String}

```
インデックス情報を含むStan変数のカンマ区切りリスト。
例えば、`array[2] real foo`はStanの.csvファイルでは
`..., foo.1, foo.2, ...`として表されます。
```

## 戻り値

OrderedDict[String, Variable]

```
各変数の基本名を構造体`Variable`にマッピングする辞書。
```

エクスポート済み。
