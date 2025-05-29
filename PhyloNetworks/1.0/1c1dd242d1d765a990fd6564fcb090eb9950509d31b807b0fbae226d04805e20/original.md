```
treeedgecomponents(net::HybridNetwork)
```

Return the tree-edge components of the semidirected network as a `membership` dictionary `Node => Int`. Nodes with the same membership integer value are in the same tree-edge component. The tree-edge components of a network are the connected components of the network when all hybrid edges are removed.

A `RootMismatch` error is thrown if there exists a cycle in any of the tree-edge components, or if a tree-edge component has more than one "entry" hybrid node.

Warnings:

  * since `Node`s are mutable, the network should not be modified until usage of the output `membership` dictionary is over.
  * the component IDs are not predicable, but will be consecutive integers from 1 to the number of components.
