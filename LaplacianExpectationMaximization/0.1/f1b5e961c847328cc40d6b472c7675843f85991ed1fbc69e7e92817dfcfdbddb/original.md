```
Optimizer(; optimizer = OptimOptimizer(Optim.LBFGS()), finetuner = nothing, fallback = OptimisersOptimizer())
```

Default optimizer. `finetuner` can be another optimizer that is called after the first `optimizer` finished. The `fallback` optimizer is called, if the `optimizer` or `finetuner` fails.

Can also be constructed as

```
Optimizer(optimizer; finetuner = nothing, fallback = OptimisersOptimizer(), kw...)
```

where `optimizer` can be a symbol (to use NLopt), or an optimiser from Optim or Optimiser. See also [`NLoptOptimizer`](@ref), [`OptimOptimizer`](@ref), [`OptimisersOptimizer`](@ref).
