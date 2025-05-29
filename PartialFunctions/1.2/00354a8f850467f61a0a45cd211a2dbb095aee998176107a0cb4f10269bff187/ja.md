```
@$ f(args...; kwargs...)
```

与えられた引数を `f` に部分的に適用します。未知の引数は `_` で表されます。

!!! note
    `_` が存在しない場合、関数は即座に実行されます。


# 例

```julia-repl
julia> matmul(A, X, B; C = 1) = A * X .+ B .* C
matmul (generic function with 1 method)

julia> A = randn(2, 2); B = rand(2, 2); X = randn(2, 2);

julia> pf = @$ matmul(_, X, _; C = 2)
matmul(_, X, _; C = 2)

julia> pf(A, B) ≈ matmul(A, X, B; C = 2)
true
```
