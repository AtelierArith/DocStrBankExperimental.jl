```
grad(w::Nodes{Dual}) --> Edges{Dual}
```

Evaluate the discrete gradient of dual nodal data `w`. Can also perform this operation by creating an object of Grad type and applying it with `*`.
