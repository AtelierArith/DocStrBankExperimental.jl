```
divergence!(w::Edges,q::EdgeGradient)
```

Evaluate the discrete divergence of edge gradient tensor data `q` and return it as data `w`. Note that `q` can be either primal/dual or dual/primal tensor data, and `w` must be, respectively, primal or edges type.
