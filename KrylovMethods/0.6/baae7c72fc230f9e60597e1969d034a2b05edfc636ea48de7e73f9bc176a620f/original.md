x,flag,err,iter,resvec = gmres(A,b,restrt,tol=1e-2,maxIter=100,M=1,x=[],out=0)

Generalized Minimal residual ( GMRESm ) method with restarts applied to A*x = b.

Input:

A       - function computing A*x    b       - right hand side vector   restrt  - number of iterations between restarts   tol     - error tolerance   maxIter - maximum number of iterations   M       - preconditioner, function computing M\x   x       - starting guess   out     - flag for output (0 : only errors, 1 : final status, 2: error at each iteration)

Output:

x       - approximate solution   flag    - exit flag (  0 : desired tolerance achieved,                         -1 : maxIter reached without converging                         -9 : right hand side was zero)   err     - norm of relative residual, i.e., norm(A*x-b)/norm(b)   iter    - number of iterations   resvec  - norm of relative residual at each iteration
