```
@decorators [separators=nothing] [parentheses=nothing] expr
```

指定されたデコレータ文字列を `kwargs` で使用して `expr` を実行します。

提供される場合、`separators` は `(key1=value1, ...)` の形式でなければならず、提供された値は `String` 型に解決される必要があります。提供される場合、`parentheses` は `(key1=value1, ...)` の形式でなければならず、提供された値は `Tuple{String, String}` 型に解決される必要があります。

# 引数

## セパレーター

  * `horiz` - アイテムを水平に結合する際に使用されるセパレーター文字列
  * `kv` - `KeyValue` ペアをレンダリングする際に使用されるセパレーター文字列
  * `pair` - `Pair` オブジェクトをレンダリングする際に使用されるセパレーター文字列

## 括弧

  * `vector` - `AbstractVector` をレンダリングする際に使用される開始 + 終了の括弧
  * `set` - `AbstractSet` をレンダリングする際に使用される開始 + 終了の括弧
  * `dict` - `AbstractDict` および `AbstractDictionary` をレンダリングする際に使用される開始 + 終了の括弧
  * `tuple` - `Tuple` をレンダリングする際に使用される開始 + 終了の括弧
  * `named_tuple` - `NamedTuple` をレンダリングする際に使用される開始 + 終了の括弧
