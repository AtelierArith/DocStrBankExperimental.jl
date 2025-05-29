```
fit_rbf(xv::Array, yv::Array, cp::Array)
```

fit thin-plate radial basis function according to:

```
`xv` : array NxP, N number of training points, P number of input variables

`yv` : array NxQ, N number of training points, Q number of output variables

`cp` : array KxP, K number of control points, P number of input variables
```

returns a callable RBF object.
