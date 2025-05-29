```
group([keyf=identity], X; [restype=Dictionary])
```

Group elements of `X` by `keyf(x)`, returning a mapping `keyf(x)` values to lists of `x` values in each group.

The result is an (ordered) `Dictionary` by default, but can be specified to be a base `Dict` as well.

Alternatively to dictionaries, specifying `restype=KeyedArray` (from `AxisKeys.jl`) results in a `KeyedArray`. Its `axiskeys` are the group keys.

# Examples

```julia
xs = 3 .* [1, 2, 3, 4, 5]
g = group(isodd, xs)
g == dictionary([true => [3, 9, 15], false => [6, 12]])


g = group(x -> (a=isodd(x),), xs; restype=KeyedArray)
g == KeyedArray([[6, 12], [3, 9, 15]]; a=[false, true])
```
