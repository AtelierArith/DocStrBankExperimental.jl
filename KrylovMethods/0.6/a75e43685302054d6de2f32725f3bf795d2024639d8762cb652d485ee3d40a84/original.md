x,flag,err,iter,resvec = ssor(A::SparseMatrixCSC, b::Vector; omega::Real=2/3, tol::Real=1e-2, maxIter::Int=1,out::Int=0)

Symmetric successive over-relaxation applied to the linear system A*x = b.

!! Note that upper/lower triangular matrix are never build to save memory !!

Input:

```
A       - sparse matrix CSC
b       - right hand side vector
omega   - relaxation parameter (omega=1.0: Gauss Seidel)
tol     - error tolerance (default=1e-2)
maxIter - maximum number of iterations (default=1)
out     - flag for output (-1 : no output, 0 : only errors, 1 : final status, 2: error at each iteration)
```

Output:

```
x       - solution
flag    - exit flag (  0 : desired tolerance achieved,
                      -1 : maxIter reached without converging)
err     - error, i.e., norm(A*x-b)/norm(b)
iter    - number of iterations
resvec  - error at each iteration
```
