```
@OptionalData name type msg=""
```

Initialise a constant `name` with type `OptData{type}`. An exception with the custom error message `msg` is thrown when `name` is accessed before data has been pushed to it.

# Example

```julia
@OptionalData OPT_FLOAT Float64
```
