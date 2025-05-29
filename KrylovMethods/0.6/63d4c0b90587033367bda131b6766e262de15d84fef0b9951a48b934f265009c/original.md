x,flag,err,iter,resvec = cg(A,b,tol=1e-2,maxIter=100,M=1,x=[],out=0)

(Preconditioned) Conjugate Gradient applied to the linear system A*x = b, where A is assumed  to be symmetric positive semi definite.

Input:

A       - matrix or function computing A*x   b       - right hand side vector   tol     - error tolerance   maxIter - maximum number of iterations   M       - preconditioner, a function that computes M\x   x       - starting guess   out     - flag for output (-1: no output, 0: only errors, 1: final status, 2: residual norm at each iteration)

Output:

x       - approximate solution   flag    - exit flag ( 0 : desired tolerance achieved,   					 -1 : maxIter reached without converging   					 -2 : Matrix A is not positive definite   					 -3 : cg stalled, i.e. two consecutive residuals have same norm   					 -9 : right hand side was zero)   err     - norm of relative residual, i.e., norm(A*x-b)/norm(b)   iter    - number of iterations   resvec  - norm of relative residual at each iteration
