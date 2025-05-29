```
nodes(t; skiproot=false)
leaves(t)
internals(t; skiproot=false)
```

ツリーのすべてのノード / 葉 / 内部ノードに対するイテレータ。`skiproot`が指定されている場合、イテレータはルートノードをスキップします。

# 注意

`internals(t)`に対して`length`を呼び出すことはできません。なぜなら、後者は`Iterators.filter`に基づいているからです。ツリーの内部ノードの数を取得する方法の一例は、`length(nodes(t)) - length(leaves(t))`を呼び出すことです。
