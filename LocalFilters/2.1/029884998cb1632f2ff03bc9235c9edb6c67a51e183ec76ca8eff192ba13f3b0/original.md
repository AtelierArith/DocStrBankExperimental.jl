```
FORWARD_FILTER
```

is an exported constant object used to indicate *forward* ordering of indices in local filter operations. It can be called as:

```
FORWARD_FILTER(i, j) -> j - i
```

to yield the index in the filter kernel. See also [`REVERSE_FILTER`](@ref) for *reverse* ordering and [`LocalFilters.localindices`](@ref) for building a range of valid indices `j`.
