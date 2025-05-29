```
wrap(f::Function; time_agnostic=true)
```

Return a callable object that acts on nodes, and returns a node.

It is assumed that `f` is stateless (this will therefore not work with closures). We also assume that we will always emit a knot when the alignment semantics say we should — thus `f` must always return a valid output value.

Iff `time_agnostic` is `false`, `f` will be passed the time of the current knot as the first argument, followed by the value of every input.

If the object is called with more than one node, alignment will be performed. If an alignment other than the default should be used, provide it as the final argument.

Internally this will call `TimeDag.apply(f, args...; kwargs...)`; see there for further details.
