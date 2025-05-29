```
@copy(<source>, <destination>)
```

Macro for copying the value of a random choice (or a whole namespace of random choices) from an input trace to an output trace in the [Trace Transform DSL](@ref).

<destination> is of the form <trace>[<addr>] where <trace> is an input trace, and <annotation> is either :discrete or :continuous.
