```
ghostlayer(forest::Pxest{X}; connection=P4estTypes.CONNECT_FULL(Val(X)))
```

Construct a ghost layer of quadrants that neighbor the local to the rank for the given `forest`.  Here `connection` determines what neighboring quadrants to include (across face, edge, corner, or full) and can take the values:

  * `P4estTypes.CONNECT_FULL(Val(4))`: get face and corner neighbors.
  * `P4estTypes.CONNECT_FULL(Val(8))`: get face, edge, and corner neighbors.
  * `P4estTypes.CONNECT_FACE(Val(4))`: get face neighbors.
  * `P4estTypes.CONNECT_FACE(Val(8))`: get face neighbors.
  * `P4estTypes.CONNECT_EDGE(Val(8))`: get face and edge neighbors.
  * `P4estTypes.CONNECT_CORNER(Val(4))`: get face and corner neighbors.
  * `P4estTypes.CONNECT_CORNER(Val(8)):`get face, edge, and corner neighbors.
