```
createpriority(T::Type{<:AbstractDataTransformer})
```

The priority with which a transformer of type `T` should be created. This can be any integer, but try to keep to -100–100 (see `create`).
