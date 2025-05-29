```
getnodeages(net)
```

vector of node ages in pre-order, as in `vec_node`.

*Warnings*: `net` is assumed to

  * have been preordered before (to calculate `vec_node`)
  * be time-consistent (all paths to the root to a given hybrid have the same length)
  * be ultrametric (all leaves have the same age: 0)
