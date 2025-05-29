```
get_observables(m::EFTfitterModel)
```

Returns a `NamedTuple` with the `Observable`s in the `EFTfitterModel`. Note: The upper and lower limits are ignored and for each unique `Function`s only one `Observable` is returned.
