```
next_bus_above_with_outdegree_more_than_one(g::MetaGraphsNext.MetaGraph, b::String)
```

`b`の上にある出次数が1より大きい次のバスを見つけます。見つからない場合は`nothing`が返されます。`b`の上に入次数が1より大きいバスが見つかった場合はエラーが発生します。
