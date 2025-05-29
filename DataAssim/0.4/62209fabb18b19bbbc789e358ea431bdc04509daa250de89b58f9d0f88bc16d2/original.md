```
x,J = fourDVar(
        xi,Pi,ℳ,yo,R,H,nmax,no;
        innerloops = 10,
        outerloops = 2,
        tol = 1e-5)
```

Incremental 4D-Var with the model `ℳ` (`AbstractModel`) and `nmax` time-steps starting at the initial condition `xi` and error covariance `Pi` with the specified numbers of inner and outer loops. Observations `yo` (vector of vectors) and error covariance `R` (vector of matrices) at the time steps given in `no` are assimilated with the observation operator `H` (`AbstractModel`).
