```
dropdown(options::AbstractObservable;
         value = first(values(options[])),
         label = nothing,
         multiple = false)
```

A dropdown menu whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = dropdown(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
