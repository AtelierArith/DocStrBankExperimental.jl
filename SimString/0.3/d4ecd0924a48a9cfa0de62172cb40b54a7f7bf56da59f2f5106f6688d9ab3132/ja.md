```
DictDB(x::WordNGrams)
```

WordNGramsのための追加のコンテナとメタデータを持つ辞書DBを初期化します。

# 引数

  * `x`: WordNGramsオブジェクト

# 例

```julia
db = DictDB(WordNGrams(2, " ", " "))
```

# 戻り値

  * `DictDB`: WordNGramsのための追加のコンテナとメタデータを持つDictDBオブジェクト
