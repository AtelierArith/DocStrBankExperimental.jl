```
pop(s::S, x) where S <: SmallBitSet -> Tuple{S, Int}
```

ペア `(t, x)` を返します。ここで `t` は `x` が削除されたセット `s` です。セット `s` は空であってはなりません。

`Base.pop!`、`BangBang.pop!!` も参照してください。
