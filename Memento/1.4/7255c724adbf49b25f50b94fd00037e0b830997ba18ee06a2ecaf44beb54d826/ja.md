```
DictFormatter([aliases, serializer])
```

レコードをJSONなどのシリアライズ形式に適したDictにフォーマットし、生成された辞書に対してシリアライザ関数を実行します。

# 引数

  * `aliases::Dict{Symbol, Symbol}`: キーがエイリアスを表し、値が辞書に含める既存のレコード属性を表すマッピング（デフォルトですべての属性）。
  * `serializer::Function`: 辞書を受け取り、文字列を返す関数。デフォルトは`string(dict)`です。
