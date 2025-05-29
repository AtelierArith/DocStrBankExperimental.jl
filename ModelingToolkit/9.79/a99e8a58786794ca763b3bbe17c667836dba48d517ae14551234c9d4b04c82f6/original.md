```julia
toggle_namespacing(
    sys::ModelingToolkit.AbstractSystem,
    value::Bool;
    safe
) -> Any

```

Return a new `sys` with namespacing enabled or disabled, depending on `value`. The keyword argument `safe` denotes whether systems that do not support such a toggle should error or be ignored.
