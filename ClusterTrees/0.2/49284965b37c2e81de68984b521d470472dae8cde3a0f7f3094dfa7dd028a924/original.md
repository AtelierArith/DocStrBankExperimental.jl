```
update!(f, tree, state, data, target)
```

Algorithm to update or add data to the tree. `router!` and `updater!` are user supplied functions:

```
route!(tree, state, target)
```

Returns the next candidate `node` until the node for insertion is reaches. Note that this function potentially created new nodes. Arrival at the destination is indicated by returning the same node that was passed as the second argument.

```
f(tree, node, data)
```

Update the destination node `node`. Typically, `data` is added in some sense to the data residing at the desitination node.
