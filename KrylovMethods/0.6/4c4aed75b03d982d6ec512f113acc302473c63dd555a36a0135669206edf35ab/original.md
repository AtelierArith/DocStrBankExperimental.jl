blockCG(A,B,X)

Preconditioned Conjugate Gradient Method for solving

A * X = B

Input:

```
A           - matrix or function computing A*x
B           - array of right hand sides
tol         - error tolerance
maxIter     - maximum number of iterations
M           - preconditioner, a function that computes M\x
X           - array of starting guesses (will be overwritten)
out         - flag for output (-1: no output, 0: only errors, 1: final status, 2: residual norm at each iteration)
ortho       - flag for re-orthogonalization (default: false)
pinvTol     - tolerance for pseudoinverse (default: eps(T)*size(B,1))
storeInterm - flag for storing iterates (default: false)
```

Output:

X       - approximate solutions (2D array if !storeInterm, 3D array else)   flag    - exit flag ( 0 : desired tolerance achieved,   					 -1 : maxIter reached without converging   					 -9 : right hand side was zero)   err     - norm of relative residual, i.e., norm(A*X-B)/norm(B)   iter    - number of iterations   resvec  - norm of relative residual at each iteration

Reference:

```
O'Leary, D. P. (1980). The block conjugate gradient algorithm and related methods.
Linear Algebra and Its Applications, 29, 293–322. http://doi.org/10.1016/0024-3795(80)90247-5
```
