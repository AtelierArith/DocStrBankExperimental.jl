```
isrootof(node, net)
```

`true` なら `node` は `net` のルートである（またはネットワークが半有向と見なされる場合にネットワークトラバーサルに使用される）；それ以外の場合は `false`。

```
isleaf(node)
isexternal(edge)
```

`true` なら `node` はリーフであるか、`edge` はリーフに隣接している；それ以外の場合は `false`。

参照: [`getroot`](@ref), [`getparent`](@ref), [`getchild`](@ref)
