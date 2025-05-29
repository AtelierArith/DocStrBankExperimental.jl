```julia
conjgrad(A, b, x0=vzeros(b)) -> x
```

solves the symmetric linear system `A⋅x = b` starting at `x0` by means of the iterative conjugate gradient method.  The returned solution `x` is a new object similar to `b` and to `x0`.

Argument `A` implements the symmetric positive definite linear mapping `A`, it can be provided as a Julia array (interpreted as a general matrix, see [`GeneralMatrix`](@ref)), as an instance of [`LinearMapping`](@ref) or as a callable object (like a function) which is used as:

```julia
A(dst, src)
```

to overwrite `dst` with `A⋅src`.  If `A` has been implemented as a callable object, such that `A(x)` yields `A⋅x`, then call `conjgrad` with an inline function:

```julia
conjgrad((dst,src) -> (dst .= A(src); return dst), b, ...)
```

See [`conjgrad!`](@ref) for accepted keywords and more details.
