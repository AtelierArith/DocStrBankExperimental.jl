EllEnsemble(X::Matrix{T},k :: Kernel)

Construct a full-rank ensemble from a set of points and a kernel function.

X is vector of column vectors (ColVecs) or a vector of row vectors (RowVecs) k is a kernel (see doc for package KernelFunctions.jl)

Example: points in 2d along the circle, and an exponential kernel

```
t = LinRange(-pi,pi,10)'
X = vcat(cos.(t),sin.(t))
using KernelFunctions
L=EllEnsemble(ColVecs(X),ExponentialKernel())
```
