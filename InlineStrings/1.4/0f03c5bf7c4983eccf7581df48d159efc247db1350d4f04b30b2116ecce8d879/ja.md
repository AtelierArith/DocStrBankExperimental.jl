```
inlinestrings(itr) => Vector

`AbstractString` 値の任意のイテレータを受け取り、
```

単一の昇格された `InlineString` 型を持つ `Vector` を生成しようとします。つまり、すべてのイテレートされた要素は、すべての要素を収容できる最小の `InlineString` サブタイプに昇格されます。現在の最大の InlineString 型（256 バイト）よりも大きい値がある場合、コレクション全体は代わりに `String` に昇格されます。`missing` 値も許可されており、結果の eltype は `Union{Missing, X}` となり、ここで `X` は `InlineString` サブタイプまたは `String` です。
