```
wrapdims(A, T, keyvecs...)
wrapdims(A, T; name=keyvec...)
```

This applies type `T` to all of the keys, for example to wrap them as `UniqueVector`s or `AcceleratedArray`s (using those packages) for fast lookup.
