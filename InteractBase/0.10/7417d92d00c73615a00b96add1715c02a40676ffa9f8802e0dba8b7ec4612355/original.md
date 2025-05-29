`tabs(options::AbstractDict; value::Union{T, Observable})`

Creates a set of tabs whose labels are the keys of options. The label can be a link.

`tabs(values::AbstractArray; kwargs...)`

`tabs` with labels `values` see `tabs(options::AbstractDict; ...)` for more details

```
tabs(options::AbstractObservable; kwargs...)
```

Tabs whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = tabs(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
