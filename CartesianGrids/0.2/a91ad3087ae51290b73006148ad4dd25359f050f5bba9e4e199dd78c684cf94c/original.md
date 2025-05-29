```
grad!(d::EdgeGradient{Dual,Primal},q::Edges{Dual})
```

Evaluate the discrete gradient of dual edge data `q` and return it as edge gradient data `d`, where the diagonal entries of the gradient lie on dual nodes and the off-diagonal entries lie at primal nodes.
