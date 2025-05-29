```
DictDB(x::CharacterNGrams)
```

CharacterNGramsのための追加のコンテナとメタデータを持つ辞書DBを初期化します。

# 引数

  * `x`: CharacterNGramsオブジェクト

# 例

```julia
db = DictDB(CharacterNGrams(2, " "))
```

# 戻り値

  * `DictDB`: CharacterNGramsのための追加のコンテナとメタデータを持つDictDBオブジェクト
