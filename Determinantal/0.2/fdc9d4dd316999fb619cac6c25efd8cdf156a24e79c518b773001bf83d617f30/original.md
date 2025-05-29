```
nystrom_approx(x :: AbstractVector,ker :: Kernel,ind)
```

Compute a low-rank approximation of a kernel matrix (with kernel "ker") using the rows and columns indexed by "ind".

```@example
using KernelFunctions
x = rand(2, 100)
K = kernelmatrix(SqExponentialKernel(), ColVecs(x))
#build a rank 30 approx. to K
V = nystrom_approx(ColVecs(x), SqExponentialKernel(), 1:30)
norm(K - V * V') #should be small
```
