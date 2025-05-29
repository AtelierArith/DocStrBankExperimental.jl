```
Prometheus.@inprogress collector expr
```

Track the number of concurrent in-progress evaluations of `expr`. From the builtin collectors this is only applicable to the [`Gauge`](@ref) – the value of the gauge is incremented with 1 when entering the section, and decremented with 1 when exiting the section.

The expression, `expr`, can be a single expression (for example a function call), or a code block (`begin`, `let`, etc), e.g.

```julia
Prometheus.@inprogress collector <expr>

Prometheus.@inprogress collector begin
    <expr>
end
```

It is also possible to apply the macro to a function *definition*, i.e.

```julia
Prometheus.@inprogress collector function track_this(args...)
    # function body
end
```

to track number of concurrent in-progress calls (covering all call sites).
