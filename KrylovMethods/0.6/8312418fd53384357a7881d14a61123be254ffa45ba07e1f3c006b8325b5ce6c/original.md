x,flag,err,iter,resvec = cg(A,b,tol=1e-2,maxIter=100,x=[],storeInterm=false,out=0)

CGLS Conjugate gradient algorithm applied implicitly to the normal equations 

```
	(A'*A) x = A'*b.
```

Input:

A            - function computing A*x = A(x,'F') and A'*x = A(x,'T')   b            - right hand side vector   tol          - error tolerance, default 1e-2   maxIter      - maximum number of iterations, default 100   x            - starting guess   storeInterm  - flag for returning intermediate solutions (useful in inverse problems)   out          - flag for output (-1: no output, 0 : only errors, 1 : final status, 2: error at each iteration)

Output:

x       - approximate solution (interm==0) or history of approximate solutions (interm==1)   flag    - exit flag (  0 : desired tolerance achieved,                         -1 : maxIter reached without converging                         -2 : Matrix A is not positive definite                          -9 : right hand side was zero)   eta     - residual norm: norm(A*x-b)   rho     - norm of current iterate: norm(x)
