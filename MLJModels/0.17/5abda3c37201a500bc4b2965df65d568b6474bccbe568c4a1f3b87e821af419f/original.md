```
info(model::Model)
```

Return the metadata (trait values) associated with the specified `model`.

This is equivalent to `info(name; pkg=pkg)` where `name::String` is the name of the model type, and `pkg::String` the name of the core algorithm-providing package (assuming the model registry is up-to-date).
