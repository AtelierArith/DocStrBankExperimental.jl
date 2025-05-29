```
@dropdims sum(A; dims=1)
```

Macro which wraps such reductions in `dropdims(...; dims=1)`. Allows `sum(A; dims=1) do x stuff end`, and works on whole blocks of code like `@views`. Does not handle other keywords, like `reduce(...; dims=..., init=...)`.
