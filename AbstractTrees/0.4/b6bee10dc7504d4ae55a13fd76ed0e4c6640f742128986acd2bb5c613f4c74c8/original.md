```
nodevalue(tree, node_index)
```

Get the value of the node specified by `node_index` from the indexed tree object `tree`.

By default, this falls back to `tree[node_index]`.

**OPTIONAL**: Indexed trees only require this if the fallback to `getindex` is not sufficient.
