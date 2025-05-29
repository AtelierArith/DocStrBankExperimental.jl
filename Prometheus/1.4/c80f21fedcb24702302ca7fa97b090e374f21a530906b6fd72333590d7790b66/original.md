```
Prometheus.@time collector expr
```

Time the evaluation of `expr` and send the elapsed time in seconds to `collector`. The specific action depends on the type of collector:

  * `collector :: Gauge`: set the value of the gauge to the elapsed time ([`Prometheus.set`](@ref))
  * `collector :: Histogram` and `collector :: Summary`: add the elapsed time as an observation ([`Prometheus.observe`](@ref))

The expression to time, `expr`, can be a single expression (for example a function call), or a code block (`begin`, `let`, etc), e.g.

```julia
Prometheus.@time collector <expr>

Prometheus.@time collector begin
    <expr>
end
```

It is also possible to apply the macro to a function *definition*, i.e.

```julia
Prometheus.@time collector function time_this(args...)
    # function body
end
```

to time every call to this function (covering all call sites).
