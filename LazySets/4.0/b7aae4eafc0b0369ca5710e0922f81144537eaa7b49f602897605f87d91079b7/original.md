```
isempty_known(cap::Intersection)
```

Ask whether the status of emptiness is known.

### Input

  * `cap` – intersection of two sets

### Output

`true` iff the emptiness status is known. In this case, `isempty(cap)` can be used to obtain the status in constant time.
