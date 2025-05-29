```
mapflat(f, collection; maptype::Type=Union{NamedTuple,Tuple,AbstractArray})
```

"Flattened" version of `map` where `f` is applied to all nested non-collection elements of `x`. The transformed result is returned with the nested structure of the input `x` unchanged. Note that this differs from `flatmap` in functional settings, which is typically just `map` followed by `flatten`.

# Examples

```julia-repl
julia> mapflat(x -> 2*x, (a = (b = (1,)), c = (d = (2,))))
(a = (b = (2,)), c = (d = (4,)))
```
