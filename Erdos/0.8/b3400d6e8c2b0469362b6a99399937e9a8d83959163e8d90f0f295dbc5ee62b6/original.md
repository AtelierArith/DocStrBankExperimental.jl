```
label_propagation(g; maxiter=1000)
```

Community detection using the label propagation algorithm (see [Raghavan et al.](http://arxiv.org/abs/0709.2938)). `g` is the input Graph, `maxiter` is the  maximum number of iterations. Returns a vertex assignments and the convergence history
