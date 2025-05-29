```
connect(from::AbstractReteNode, to::AbstractReteNode)
```

makes `to` an output of `from` and `from` an input of `to`.

`connect` calls [`_add_input`](@ref) and [`_add_output`](@ref) to do this.
