```
to_toml(x; sorted=false, by=identity, kw...)
```

Convert an instance `x` of option type to TOML and write it to `String`. See also `TOML.print`. 

`to_toml` does not export fields that are of the same values as the defaults. This can be  overridden by changing `include_defaults` to `true`.
