```
convert_to_dataset(obj; group = :posterior, kwargs...) -> Dataset
```

Convert a supported object to a [`Dataset`](@ref).

In most cases, this function calls [`convert_to_inference_data`](@ref) and returns the corresponding `group`.
