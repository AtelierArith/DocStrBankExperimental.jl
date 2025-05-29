```
getresult(thunk::Thunk)
```

Get the result of a `Thunk`. If `thunk` has not been reified, return `nothing`, else return a `Some`-wrapped result.
