```
jump_nnls(order, solver)
```

Jump non-negative least squares method for tikhonov (L2) regularization,  implemented using the JuMP extension. All around effective, but can be slow for large problems, such as 2D inversions,  unless a powerful solver like gurobi is used. The solver argument is parsed directly into JuMP. It can be used as a "solver" for invert function. Order determines the tikhonov matrix. If 0 is chosen, the identity matrix is used.
