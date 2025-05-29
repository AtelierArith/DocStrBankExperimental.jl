```
to_dict(x, option::ToDictOption) -> OrderedDict
```

Convert an object `x` to an `OrderedDict` with `ToDictOption` specified.

# Example

```julia
to_dict(x, TOMLStyle) # TOML compatible
to_dict(x, YAMLStyle) # YAML compatible
to_dict(x, JSONStyle) # JSON compatible
```
