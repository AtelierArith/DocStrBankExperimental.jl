```
@nested_log(symbol, expr)
```

A macro that enables us to log data in a nested sense.

# Examples

  * Example 1

```julia
@nested_log :subsystem dynamics!(dx.sub, x.sub, p.sub, t)
```

will log data from `dynamics!(dx.sub, x.sub, p.sub, t)` as `__LOGGER__.subsystem`.

  * Example 2

```julia
@nested_log :subsystem state = x
```

# NOTICE

If you assign values with the two same keys, it will yield an error looks like:

```julia
ERROR: MethodError: no method matching recursive_merge(::Int64, ::Int64)
```
