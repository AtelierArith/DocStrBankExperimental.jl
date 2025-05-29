```
nodetype(::Type{T})
nodetype(node) = nodetype(typeof(node))
```

Returns a type which must be a parent type of all nodes in the tree connected to `node`.  This can be used to, for example, specify the `eltype` of any `TreeIterator` on `node`.
