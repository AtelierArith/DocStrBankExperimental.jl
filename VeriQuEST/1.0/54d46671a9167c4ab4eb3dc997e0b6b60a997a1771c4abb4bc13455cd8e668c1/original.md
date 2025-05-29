```
get_input_value(resource::MBQCResourceState, iter)
```

Returns the input value at the `iter`-th index from a given `MBQCResourceState`. If `iter` is greater than the length of the input indices, the function returns `nothing`.

# Arguments

  * `resource`: An `MBQCResourceState` from which to extract the input value.
  * `iter`: The index at which to extract the input value.

# Examples

```julia
value = get_input_value(resource, 1) # Returns the input value at the first index of the resource
```
