```
checkboxes(options::AbstractDict;
         value = valtype(options)[]
```

A list of checkboxes whose item labels are the keys of options. The observable will hold an array containing the values of all selected items, e.g. `checkboxes(OrderedDict("good"=>1, "better"=>2, "amazing"=>9001))`

`checkboxes(values::AbstractArray; kwargs...)`

`checkboxes` with labels `string.(values)` see `checkboxes(options::AbstractDict; ...)` for more details

```
checkboxes(options::AbstractObservable; kwargs...)
```

Checkboxes whose `options` are a given `Observable`. Set the `Observable` to some other value to update the options in real time.

## Examples

```julia
options = Observable(["a", "b", "c"])
wdg = checkboxes(options)
options[] = ["c", "d", "e"]
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```

To create checkboxes that are already checked off when shown, one can use the `value` keyword:

```julia
options = ["a", "b", "c"]
value = ["a", "c"]
checkboxes(options, value = value)
```

The boxes "a" and "c" will be checked off when the checkboxes widget is shown. Both `options` and `value` can be Observables.
