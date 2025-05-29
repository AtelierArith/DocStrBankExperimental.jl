```
pop(s::S) where S <: SmallBitSet -> Tuple{S, Int}
```

ペア `(t, x)` を返します。ここで `x` は `s` からの最小の要素であり、`t` は `x` が削除された集合 `s` です。集合 `s` は空であってはなりません。

`Base.pop!`、`BangBang.pop!!` も参照してください。
