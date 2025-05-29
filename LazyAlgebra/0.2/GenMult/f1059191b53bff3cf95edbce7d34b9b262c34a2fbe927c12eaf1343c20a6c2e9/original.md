# Lazily Generalized Matrix-Vector mutiplication

```julia
lgemv([α=1,] [tr='N',] A, x) -> y
```

yields `y = α*op(A)*x` where `op(A)` is `A` if `tr` is `'N'`, `transpose(A)` if `tr` is `'T'` and `adjoint(A)` if `tr` is `'C'`.  The expression `op(A)*x` is a matrix-vector multiplication but interpreted by grouping consecutive dimensions of `A` and `x` as follows:

  * if `tr` is `'N'`, the trailing dimensions of `x` must match those of `A` and the leading dimensions of `A` are those of the result `y`;
  * if `tr` is `'T'` or `'C'`, the leading dimensions of `x` must match those of `A` and the trailing dimensions of `A` are those of the result `y`.

The in-place version is called by:

```julia
lgemv!([α=1,] [tr='N',] A, x, [β=0,] y) -> y
```

and overwrites the contents of `y` with `α*op(A)*x + β*y`.  Note that `x` and `y` must not be aliased.

The multipliers `α` and `β` must be both specified or omitted, they can be any scalar numbers but are respectively converted to `promote_eltype(A,x)` and `eltype(y)` which may throw an `InexactError` exception.

See also: [`lgemm`](@ref), [`LinearAlgebra.BLAS.gemv`](@ref), [`LinearAlgebra.BLAS.gemv!`](@ref).
