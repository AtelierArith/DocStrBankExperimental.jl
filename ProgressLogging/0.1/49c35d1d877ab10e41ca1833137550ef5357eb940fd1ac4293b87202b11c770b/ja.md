```
@logprogress [name] progress [key1=val1 [key2=val2 ...]]
```

このマクロは[`@withprogress`](@ref)マクロの内部で使用する必要があります。

値`progress`で進捗イベントをログします。式`progress`は、`0`と`1`（両端を含む）の間の実数、`NaN`、または文字列`"done"`として評価される必要があります。

オプションの最初の引数`name`は、進捗バーの名前を変更するために使用できます。追加のキーワード引数は`@logmsg`に渡されます。
