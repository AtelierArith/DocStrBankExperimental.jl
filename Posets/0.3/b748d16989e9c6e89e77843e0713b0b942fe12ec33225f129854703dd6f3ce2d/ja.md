```
add_relation!(p::Poset, a::Integer, b::Integer)::Bool
```

`a<b` を順序集合に関係として追加します。成功した場合は `true` を返します。

これは次のようにも呼び出すことができます：

  * `add_relation!(p, (a, b))`
  * `add_relation!(p, a => b)`
