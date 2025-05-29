```
toggles(options::AbstractDict;
         value = first(values(options)))
```

A list of toggle switches whose item labels are the keys of options. Tthe observable will hold an array containing the values of all selected items, e.g. `toggles(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`toggles(values::AbstractArray; kwargs...)`

`toggles` with labels `string.(values)` see `toggles(options::AbstractDict; ...)` for more details

```
toggles(options::AbstractObservable; kwargs...)
```

Toggles whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = toggles(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
