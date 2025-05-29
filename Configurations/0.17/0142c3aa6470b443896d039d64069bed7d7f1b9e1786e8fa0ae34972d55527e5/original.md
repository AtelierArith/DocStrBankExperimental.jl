```
to_toml([f::Function], filename::String, option; sorted=false, by=identity, kw...)
```

Convert an instance `option` of option type to TOML and write it to `filename`. See also `TOML.print`.
