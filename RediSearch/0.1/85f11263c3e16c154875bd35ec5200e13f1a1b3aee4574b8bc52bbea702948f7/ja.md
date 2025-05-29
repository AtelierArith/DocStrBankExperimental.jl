```
TextField(name; weight=1.0, no_stem=false, phonetic=nothing, kwargs...)
```

TextFieldを作成します。

# 引数

  * `name`: フィールドの名前。

# キーワード

  * `weight`: フィールドの重み。
  * `no_stem`: ステムのブール値。
  * `phonetic`: 音声的参照。
  * `kwargs...`: `Field`オブジェクトで定義された追加フィールド。

# 戻り値

  * `TextField::Field`
