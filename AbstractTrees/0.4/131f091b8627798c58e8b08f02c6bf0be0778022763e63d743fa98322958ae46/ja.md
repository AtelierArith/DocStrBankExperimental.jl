```
NonIndexedChildren <: ChildIndexing
```

`children(n)`によって返されるオブジェクトは、`n`がツリーノードである場合、必ずしもインデックス可能であるとは限らないことを示します。この特性は、特定のケースでツリーがインデックス可能であるかどうかに関係なく、すべてのケースでインデックス可能な子を保証できないツリーに適用されます。たとえば、`Array`は、この特性を持っていますが、配列からなるインデックス可能なツリーの大きなクラスがあります。
