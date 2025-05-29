```
REVERSE_FILTER
```

is an exported constant object used to indicate *reverse* ordering of indices in local filter operations. It can be called as:

```
REVERSE_FILTER(i, j) -> i - j
```

to yield the index in the filter kernel. See also [`FORWARD_FILTER`](@ref) for *forward* ordering and [`LocalFilters.localindices`](@ref) for building a range of valid indices `j`.
