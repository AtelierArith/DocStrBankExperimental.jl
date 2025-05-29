```
restyle!(gt::GenericTrace, i::Int=1, update::AbstractDict=Dict(); kwargs...)
```

Update trace `gt` using dict/kwargs, assuming it was the `i`th ind in a call to `restyle!(::Plot, ...)`
