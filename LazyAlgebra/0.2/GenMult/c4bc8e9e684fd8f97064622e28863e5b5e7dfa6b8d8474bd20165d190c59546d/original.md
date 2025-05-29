# Lazily Generalized Matrix-Matrix mutiplication

```julia
lgemm([α=1,] [transA='N',] A, [transB='N',] B, Nc=2) -> C
```

yields `C = α*op(A)*op(B)` where `op(A)` is `A` if `transA` is `'N'`, `transpose(A)` if `transA` is `'T'` and `adjoint(A)` if `transA` is `'C'` and similarly for `op(B)` and `transB`.  The expression `op(A)*op(B)` is a matrix-matrix multiplication but interpreted by grouping consecutive dimensions of `op(A)` and `op(B)` (see [`lgemv`](@ref) for explanations).  Argument `Nc` specifies the number of dimensions of the result.

The in-place version is called by:

```julia
lgemm!([α=1,] [transA='N',] A,  [transB='N',] B, [β=0,] C) -> C
```

and overwrites the contents of `C` with `α*op(A)*op(B) + β*C`.  Note that `C` must not be aliased with `A` nor `B`.

The multipliers `α` and `β` must be both specified or omitted, they can be any scalar numbers but are respectively converted to `promote_eltype(A,B)` and `eltype(C)` which may throw an `InexactError` exception.

See also: [`lgemv`](@ref), [`LinearAlgebra.BLAS.gemm`](@ref), [`LinearAlgebra.BLAS.gemm!`](@ref).
