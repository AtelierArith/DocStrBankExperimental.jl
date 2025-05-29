```
@$ f(args...; kwargs...)
```

Partially apply the given arguments to `f`. Unknown arguments are represented by `_`.

!!! note
    If no `_` is present, the function is executed immediately.


# Examples

```julia-repl
julia> matmul(A, X, B; C = 1) = A * X .+ B .* C
matmul (generic function with 1 method)

julia> A = randn(2, 2); B = rand(2, 2); X = randn(2, 2);

julia> pf = @$ matmul(_, X, _; C = 2)
matmul(_, X, _; C = 2)

julia> pf(A, B) ≈ matmul(A, X, B; C = 2)
true
```
