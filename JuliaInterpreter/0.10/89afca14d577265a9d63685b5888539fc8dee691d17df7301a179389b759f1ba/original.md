```
frame = Frame(mod::Module, ex::Expr)
```

Construct a `Frame` to evaluate `ex` in module `mod`.

This constructor can error, for example if lowering `ex` results in an `:error` or `:incomplete` expression, or if it otherwise fails to return a `:thunk`.
