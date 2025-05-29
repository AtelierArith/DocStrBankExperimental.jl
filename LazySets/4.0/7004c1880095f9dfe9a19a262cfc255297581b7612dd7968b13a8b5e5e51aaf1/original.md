```
isempty(B::Bloating)
```

Determine whether a bloated set is empty.

### Input

  * `B` – bloated set

### Output

`true` iff the wrapped set is empty.

### Notes

This implementation disregards negative bloating, which could potentially turn a non-empty set into an empty set.
