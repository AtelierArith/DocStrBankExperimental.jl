```
divergence!(w::XEdges/YEdges,q::NodePair)
```

Evaluate the discrete divergence of node pair data `q` and return it as data `w`. Note that `q` can be either primal/dual or dual/primal node data, and `w` must be, respectively, primal x-edges/dual y-edges or primal y-edges/dual x-edges type.
