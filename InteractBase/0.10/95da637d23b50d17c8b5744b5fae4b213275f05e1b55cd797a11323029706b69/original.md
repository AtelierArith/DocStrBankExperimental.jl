`mask(options; index, key)`

Only display the `index`-th element of `options`. If `options` is a `AbstractDict`, it is possible to specify which option to show using `key`. `options` can be a `Observable`, in which case `mask` updates automatically. Use `index=0` or `key = nothing` to not have any selected option.

## Examples

```julia
wdg = mask(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), index = 1)
wdg = mask(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), key = "plot")
```

Note that the `options` can be modified from the widget directly:

```julia
wdg[:options][] = ["c", "d", "e"]
```
