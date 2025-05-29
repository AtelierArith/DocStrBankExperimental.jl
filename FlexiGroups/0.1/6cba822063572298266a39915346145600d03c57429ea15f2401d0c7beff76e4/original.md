```
groupmap([keyf=identity], mapf, X; [restype=Dictionary])
```

Like `map(mapf, group(keyf, X))`, but more efficient. Supports a limited set of `mapf` functions: `length`, `first`/`last`, `only`, `rand`.
