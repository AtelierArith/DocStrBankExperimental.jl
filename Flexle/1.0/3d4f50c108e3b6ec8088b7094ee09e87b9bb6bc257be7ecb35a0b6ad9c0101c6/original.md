```
deleteat!(sampler, i)
```

Remove element `i` from `sampler` completely, updating all fields accordingly.

Returns the new number of weights in `sampler`.

All elements of index `>i` are updated to account for the removal of element `i`.
