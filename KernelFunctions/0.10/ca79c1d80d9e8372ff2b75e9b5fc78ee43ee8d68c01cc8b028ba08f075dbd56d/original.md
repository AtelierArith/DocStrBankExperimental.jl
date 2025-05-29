```
KernelProduct <: Kernel
```

Create a product of kernels. One can also use the overloaded operator `*`.

There are various ways in which you create a `KernelProduct`:

The simplest way to specify a `KernelProduct` would be to use the overloaded `*` operator. This is  equivalent to creating a `KernelProduct` by specifying the kernels as the arguments to the constructor.  

```jldoctest kernelprod
julia> k1 = SqExponentialKernel(); k2 = LinearKernel(); X = rand(5);

julia> (k = k1 * k2) == KernelProduct(k1, k2)
true

julia> kernelmatrix(k1 * k2, X) == kernelmatrix(k1, X) .* kernelmatrix(k2, X)
true

julia> kernelmatrix(k, X) == kernelmatrix(k1 * k2, X)
true
```

You could also specify a `KernelProduct` by providing a `Tuple` or a `Vector` of the  kernels to be multiplied. We suggest you to use a `Tuple` when you have fewer components   and a `Vector` when dealing with a large number of components.

```jldoctest kernelprod
julia> KernelProduct((k1, k2)) == k1 * k2
true

julia> KernelProduct([k1, k2]) == KernelProduct((k1, k2)) == k1 * k2
true
```
