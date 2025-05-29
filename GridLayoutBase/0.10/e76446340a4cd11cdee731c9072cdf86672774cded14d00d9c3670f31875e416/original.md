```
GridLayout(g::Union{GridPosition, GridSubposition}, args...; kwargs...)
```

Create a `GridLayout` at position `g` in the parent `GridLayout` of `g` if it is a `GridPosition` and in a nested child `GridLayout` if it is a `GridSubposition`. The `args` and `kwargs` are passed on to the normal `GridLayout` constructor.
