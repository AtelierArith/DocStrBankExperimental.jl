```
KernelTensorProduct
```

Tensor product of kernels.

# Definition

For inputs $x = (x_1, \ldots, x_n)$ and $x' = (x'_1, \ldots, x'_n)$, the tensor product of kernels $k_1, \ldots, k_n$ is defined as

$$
k(x, x'; k_1, \ldots, k_n) = \Big(\bigotimes_{i=1}^n k_i\Big)(x, x') = \prod_{i=1}^n k_i(x_i, x'_i).
$$

# Construction

The simplest way to specify a `KernelTensorProduct` is to use the overloaded `tensor` operator or its alias `⊗` (can be typed by `\otimes<tab>`).

```jldoctest tensorproduct
julia> k1 = SqExponentialKernel(); k2 = LinearKernel(); X = rand(5, 2);

julia> kernelmatrix(k1 ⊗ k2, RowVecs(X)) == kernelmatrix(k1, X[:, 1]) .* kernelmatrix(k2, X[:, 2])
true
```

You can also specify a `KernelTensorProduct` by providing kernels as individual arguments or as an iterable data structure such as a `Tuple` or a `Vector`. Using a tuple or individual arguments guarantees that `KernelTensorProduct` is concretely typed but might lead to large compilation times if the number of kernels is large.

```jldoctest tensorproduct
julia> KernelTensorProduct(k1, k2) == k1 ⊗ k2
true

julia> KernelTensorProduct((k1, k2)) == k1 ⊗ k2
true

julia> KernelTensorProduct([k1, k2]) == k1 ⊗ k2
true
```
