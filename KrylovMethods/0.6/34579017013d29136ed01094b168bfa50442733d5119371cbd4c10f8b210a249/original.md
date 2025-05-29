x,flag,err,iter,resvec = lsqr(A,b,;x=[],maxIter=20,atol=1e-10,btol=1e-10,condlim=1e6,out=1,doBidiag=false,                               storeInterm::Bool=false)

Least Squares QR method (LSQR) for solving 

min_x || A x - b ||,

where A is assumed is either over or underdetermined.

Implementation follows and comments refer to Algorithm LSQR in:

Paige, C. C., & Saunders, M. A. (1982).  LSQR: An Algorithm for Sparse Linear Equations and Sparse Least Squares.  ACM Transactions on Mathematical Software (TOMS), 8(1), 43–71. doi:10.1145/355984.355989

Required input:

A       - function in (flag,v,alpha,x).              if flag=='F'                   x <- A*v + alpha*x (overwrite x)             elseif flag=='T'                  x <- A'*v + alpha*x (overwriting x)             end   b       - right hand side vector

Optional input:

x           - starting guess (optional)   maxIter     - maximum number of iterations   atol        - error tolerance for (estimated) residual norm (for compatible systems)   btol        - error tolerance for (estimated) gradient norm (for incompatible systems)   condlim     - for stopping based on (estimated) condition number   out         - flag for output (-1: no output, 0: only errors, 1: final status, 2: residual norm at each iteration)   doBidiag    - returns the bidiagonalization of A at the final iteration   storeInterm - store and return intermediate iterates

Output:

x       - approximate solution  flag    - exit flag ( 0 : stopping based on atol or btol,                       -1 : maxIter reached without converging                       -2 : condition number became too large                       -9 : right hand side was zero)  his     - status at each iteration  U,S,V   - bidiagonalization (only build if doBidiag==true)
