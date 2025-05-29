x,flag,err,iter,resvec = fgmres(A,b,restrt,tol=1e-2,maxIter=100,M=1,x=[],out=0)

(flexible) Generalized Minimal residual ( (F)GMRES(m) ) method with restarts applied to A*x = b.

This is the "right preconditioning" version of GMRES: A*M^{-1}Mx = b. See gmres.jl for "left preconditioning".

Input:

A       - function computing A*x b       - right hand side vector restrt  - number of iterations between restarts tol     - error tolerance maxIter - maximum number of iterations M       - preconditioner, function computing M\x x       - starting guess out     - flag for output (0 : only errors, 1 : final status, 2: error at each iteration)

Output:

x       - approximate solution flag    - exit flag (  0 : desired tolerance achieved, 	-1 : maxIter reached without converging 	-9 : right hand side was zero) 	err     - norm of relative residual, i.e., norm(A*x-b)/norm(b) 	iter    - number of iterations 	resvec  - norm of relative residual at each iteration

```
preconditioner M(r) must return a copy of a vector. Cannot reuse memory of r.
```
