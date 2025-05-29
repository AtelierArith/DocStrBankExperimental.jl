```
peakheights(; [min, max]) -> Function
```

Create a function, `f(pks::NamedTuple)`, that copies and filters the peak heights of its argument, `pks`, using any given keyword arguments.

# Examples

```jldoctest
julia> findmaxima([0, 5, 2, 3, 3, 1, 4, 0]) |> peakheights(; max=4)
(indices = [4, 7], heights = [3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])
```
