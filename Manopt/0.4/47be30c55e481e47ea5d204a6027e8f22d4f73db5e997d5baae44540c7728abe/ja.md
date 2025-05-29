```
get_gradient(s::AbstractManoptSolverState)
```

[`AbstractManoptSolverState`](@ref)$s$内の（最後に保存された）勾配を返します。デフォルトでは、事前に状態を装飾解除します。
