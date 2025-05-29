```
KernelMatrix{Tf,Tx,Ty,T} <:: AbstractKernelMatrix{T}
```

Generic kernel matrix representing a kernel function acting on two sets of elements. If `K` is a `KernelMatrix`, then `K[i,j] = f(X[i],Y[j])` where `f::Tf=kernel(K)`, `X::Tx=rowelements(K)` and `Y::Ty=colelements(K)`.

# Examples

```julia
X = rand(SVector{2,Float64},2)
Y = rand(SVector{2,Float64},2)
K = KernelMatrix(X,Y) do x,y
    sum(x+y)
end
```
