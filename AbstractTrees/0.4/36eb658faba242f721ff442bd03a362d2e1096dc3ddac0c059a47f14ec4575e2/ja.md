```
nodetype(::Type{T})
nodetype(node) = nodetype(typeof(node))
```

`node`に接続された木のすべてのノードの親タイプでなければならない型を返します。これは、例えば、`node`上の任意の`TreeIterator`の`eltype`を指定するために使用できます。
