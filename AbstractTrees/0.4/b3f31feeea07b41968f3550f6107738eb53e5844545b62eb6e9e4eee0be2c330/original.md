```
ischild(node1, node2; equiv=(===))
```

Check if `node1` is a child of `node2`.

By default this iterates through `children(node2)`, so performance may be improved by adding a specialized method for given node type.

Equivalence is established with the `equiv` function.  New methods of this function should include this argument or else it will fall back to `===`.
