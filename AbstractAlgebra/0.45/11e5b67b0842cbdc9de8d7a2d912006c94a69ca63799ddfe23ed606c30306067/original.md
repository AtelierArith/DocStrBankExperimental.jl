```
get_attribute!(f::Function, G::Any, attr::Symbol)
```

Return the value stored for the attribute `attr` of `G`, or if no value has been set, store `key => f()` and return `f()`.

This is intended to be called using `do` block syntax.

```julia
get_attribute!(obj, attr) do
    # default value calculated here if needed
    ...
end
```
