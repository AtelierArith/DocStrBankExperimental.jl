```
radiobuttons(options::AbstractDict;
             value::Union{T, Observable} = first(values(options)))
```

e.g. `radiobuttons(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`radiobuttons(values::AbstractArray; kwargs...)`

`radiobuttons` with labels `string.(values)` see `radiobuttons(options::AbstractDict; ...)` for more details

```
radiobuttons(options::AbstractObservable; kwargs...)
```

Radio buttons whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = radiobuttons(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
