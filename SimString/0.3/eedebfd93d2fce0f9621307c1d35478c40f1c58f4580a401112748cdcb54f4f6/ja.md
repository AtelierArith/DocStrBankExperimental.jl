```
DictDB(x::MecabNGrams)
```

MecabNGramsのための追加のコンテナとメタデータを持つ辞書DBを初期化します。

# 引数

  * `x`: MecabNGramsオブジェクト

# 例

```julia
db = DictDB(MecabNGrams(2, " ", Mecab()))
```

# 戻り値

  * `DictDB`: MecabNGramsのための追加のコンテナとメタデータを持つDictDBオブジェクト
