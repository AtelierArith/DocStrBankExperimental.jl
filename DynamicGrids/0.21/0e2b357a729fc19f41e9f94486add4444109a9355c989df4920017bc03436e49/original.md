```
RunIf(f, rule)
```

`RunIf`s allows wrapping a rule in a condition, passed the `SimData` object and the cell state and index.

`$julia RunIf(dispersal) do data, state, I     state >= oneunit(state) end$ `
