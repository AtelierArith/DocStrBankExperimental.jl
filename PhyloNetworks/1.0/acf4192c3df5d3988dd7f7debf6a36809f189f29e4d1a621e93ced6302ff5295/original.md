```
isrootof(node, net)
```

`true` if `node` is the root of `net` (or used as such for network traversals in case the network is considered as semi-directed); `false` otherwise.

```
isleaf(node)
isexternal(edge)
```

`true` if `node` is a leaf or `edge` is adjacent to a leaf, `false` otherwise.

See also: [`getroot`](@ref), [`getparent`](@ref), [`getchild`](@ref)
