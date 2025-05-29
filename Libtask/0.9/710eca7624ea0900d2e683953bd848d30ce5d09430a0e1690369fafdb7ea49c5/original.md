```
set_taped_globals!(t::TapedTask, new_taped_globals)::Nothing
```

Set the `taped_globals` of `t` to `new_taped_globals`. Any calls to  [`get_taped_globals`](@ref) in future calls to `consume(t)` (either directly, or implicitly via iteration) will see this new value.
