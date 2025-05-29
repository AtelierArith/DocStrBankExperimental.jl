```
delete!(indices::AbstractIndices, i)
```

Delete the index `i` from `indices`. An error is thrown if `i` does not exist.

```
delete!(dict::AbstractDictionary, i)
```

Delete the index `i` from `dict`. An error is thrown if `i` does not exist.

See also `unset!`, `insert!`.
