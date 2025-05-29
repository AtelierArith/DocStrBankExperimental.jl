```
grad(q::Edges{Primal/Dual}) --> EdgeGradient{Dual/Primal,Primal/Dual}
```

Evaluate the discrete gradient of primal or dual edge data `q`. Can also perform this operation by creating an object of Grad type and applying it with `*`.
