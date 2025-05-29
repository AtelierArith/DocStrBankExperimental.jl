```
deletenode!(node::SkipNode)
```

Remove `node` from the list to which it belongs, update the list's length, and return the node.

The node can be at any level of the skip list, and all nodes directly above or below will also be removed.
