```
assemble_hmatrix(K::AbstractKernelMatrix[; atol, rank, rtol, kwargs...])
```

Construct an approximation of `K` as an [`HMatrix`](@ref) using the partial ACA algorithm for the low rank blocks. The `atol`, `rank`, and `rtol` optional arguments are passed to the [`PartialACA`](@ref) constructor, and the remaining keyword arguments are forwarded to the main `assemble_hmatrix` function.
