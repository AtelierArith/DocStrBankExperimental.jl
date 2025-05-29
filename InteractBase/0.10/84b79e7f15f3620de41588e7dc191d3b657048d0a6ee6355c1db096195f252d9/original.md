`tabulator(options::AbstractDict; index, key)`

Creates a set of toggle buttons whose labels are the keys of options. Displays the value of the selected option underneath. Use `index::Int` to select which should be the index of the initial option, or `key::String`. The output is the selected `index`. Use `index=0` to not have any selected option.

## Examples

```julia
tabulator(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), index = 1)
tabulator(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), key = "plot")
```

`tabulator(values::AbstractArray; kwargs...)`

`tabulator` with labels `values` see `tabulator(options::AbstractDict; ...)` for more details

```
tabulator(options::Observable; navbar=tabs, kwargs...)
```

Tabulator whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time. Defaults to `navbar=tabs`: use `navbar=togglebuttons` to have buttons instead of tabs.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = tabulator(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
