```
repr_pretty([mime], x; context=nothing)
```

`istextmime(mime)` が `true` の場合、要求された `mime` タイプで `AutoPrettyPrinting.pprint` メソッドを使用してレンダリングされた `x` の表現を含む `AbstractString` を返します。

そうでない場合は、`repr(mime, x; context)` を返します。

`mime` が提供されていない場合、デフォルトは `MIME"text/plain"` です。
