T,V = lanczosTridiag(A,b,k;tol,doReorth)

Lanczos method for getting a factorization of

A = Vk Tk Vk'

where A is a real symmetric n by n matrix, Tk is a tridiagonal k by k matrix and the columns of  the n by k matrix Vk are orthogonal.

Implementation follows:

Paige, C. C. (1972).  Computational variants of the Lanczos method for the eigenproblem.  IMA Journal of Applied Mathematics. 

Required input:

A       - function computing A*x, e.g., x -> A*x   b       - right hand side vector   k       - dimension of Krylov subspace

Optional input:

tol      - stopping tolerance   doReorth - (default=false) set to true to perform full reorthogonalization

Output:

Tk    - sparse tridiagonal matrix  Vk    - basis vectors
