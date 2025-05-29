```
minkowskinormalize(u::AbstractVector)
```

Normalizes the vector 4-vector $u$.  This does *not* check if the vector is null, in which case the result will diverge or contain `NaN`s.
