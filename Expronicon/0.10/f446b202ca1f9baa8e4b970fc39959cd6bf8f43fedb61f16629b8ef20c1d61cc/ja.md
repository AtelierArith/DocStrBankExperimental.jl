```
xcall(m::Module, name::Symbol, args...; kw...)
```

`GlobalRef(m, name)`への関数呼び出しを作成します。

!!! tip
    [Revise/#616](https://github.com/timholy/Revise.jl/issues/616)のため、マクロがReviseで動作するようにするために、ここでは`GlobalRef`の代わりにドット式`Expr(:., <module>, QuoteNode(<name>))`を使用します。

