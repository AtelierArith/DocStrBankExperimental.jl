x,flag,err,iter,resvec = bicgstb(A,b,tol=1e-6,maxIter=100,M1=1.0,M2=1.0,x=[],out=0)

BiConjugate Gradient Stabilized Method applied to the linear system Ax=b. 

Input:

A       - computing A*x   b       - right hand side vector   tol     - error tolerance   maxIter - maximum number of iterations   M1,M2   - preconditioners, either matrices or functions computing M1\x or M2\x   x       - starting guess   out     - flag for output (-1: no output, 0 : only errors, 1 : final status, 2: relres at each iteration)

Output:

x       - solution   flag    - exit flag (  	0 : desired tolerance achieved,   						-1 : maxIter reached without converging   						-2 : rho equal to zero   						-3 : norm(s)/bnrm2 < tol    						-4 : omega < 1e-16   						-9 :  right hand side was zero)   err     - error, i.e., norm(A*x-b)/norm(b)   iter    - number of iterations   resvec  - error at each iteration
