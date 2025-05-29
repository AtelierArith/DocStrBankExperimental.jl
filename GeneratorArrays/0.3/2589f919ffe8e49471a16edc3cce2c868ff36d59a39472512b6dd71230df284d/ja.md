```
array(g::<generator or iterator>)
```

`GeneratorArray(g)`型のラップされたオブジェクトを構築します。このオブジェクトは`AbstractArray`インターフェースを提供しますが、`setindex!`はサポートしていません。

ラップされたオブジェクトは、サイズが`(IteratorSize(g) == HasShape())`でなければなりません。
