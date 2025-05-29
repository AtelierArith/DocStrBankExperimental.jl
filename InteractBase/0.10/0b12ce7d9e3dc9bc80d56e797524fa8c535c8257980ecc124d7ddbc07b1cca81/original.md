`togglebuttons(options::AbstractDict; value::Union{T, Observable}, multiple=false)`

Creates a set of toggle buttons whose labels are the keys of options. Set `multiple=true` to allow multiple (or zero) active buttons at the same time.

`togglebuttons(values::AbstractArray; kwargs...)`

`togglebuttons` with labels `string.(values)` see `togglebuttons(options::AbstractDict; ...)` for more details

```
togglebuttons(options::AbstractObservable; kwargs...)
```

Togglebuttons whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = togglebuttons(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
