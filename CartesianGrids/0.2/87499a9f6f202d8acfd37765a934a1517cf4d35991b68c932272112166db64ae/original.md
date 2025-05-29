```
grad!(d::EdgeGradient{Primal,Dual},q::Edges{Primal})
```

Evaluate the discrete gradient of primal edge data `q` and return it as edge gradient data `d`, where the diagonal entries of the gradient lie on primal nodes and the off-diagonal entries lie at dual nodes.
