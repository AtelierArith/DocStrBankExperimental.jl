```
@write(<destination>, <value>, <annotation>)
```

Macro for writing the value of a random choice to an output trace in the [Trace Transform DSL](@ref).

<destination> is of the form <trace>[<addr>] where <trace> is an input trace, and <annotation> is either :discrete or :continuous.
