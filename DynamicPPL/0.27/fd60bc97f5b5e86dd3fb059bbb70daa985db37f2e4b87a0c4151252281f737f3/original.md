```
conditioned(context::AbstractContext)
```

Return `NamedTuple` of values that are conditioned on under context`.

Note that this will recursively traverse the context stack and return a merged version of the condition values.
