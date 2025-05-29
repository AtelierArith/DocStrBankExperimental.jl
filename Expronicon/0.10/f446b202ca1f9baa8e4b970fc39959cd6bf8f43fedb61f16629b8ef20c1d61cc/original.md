```
xcall(m::Module, name::Symbol, args...; kw...)
```

Create a function call to `GlobalRef(m, name)`.

!!! tip
    due to [Revise/#616](https://github.com/timholy/Revise.jl/issues/616), to make your macro work with Revise, we use the dot expression `Expr(:., <module>, QuoteNode(<name>))` instead of `GlobalRef` here.

