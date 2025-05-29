```
compute_rhs_from_function(solver, func, coefs_dofs)
```

Compute the FEM right-hand-side for a given function f and periodic splines of given degree Its components are $\int f N_i dx$ where $N_i$ is the B-spline starting at $x_i$ 

  * solver :: Maxwell solver
  * func : function
  * coefs_dofs[:]  : Finite Element right-hand-side
