```
to_dict(x; include_defaults=true, exclude_nothing=false) -> OrderedDict
```

Convert an object `x` to an `OrderedDict`.

# Kwargs

  * `include_defaults`: include the default value, default is `true`.
  * `exclude_nothing`: exclude fields that have value `nothing`,   this supersedes `include_defaults` when they are both `true`.

# Format Compatibilty

When mapping an option struct from Julia to TOML/YAML/JSON/etc. format, there are some subtle semantic compatibilty one need to deal with, we provide some convenient predefined conversion option constants as [`TOMLStyle`](@ref), [`YAMLStyle`](@ref), [`JSONStyle`](@ref).

!!! tips
    `to_dict` does not export fields that are of the same values as the defaults.  In most cases, this should be the default behaviour, and users should not use `include_defaults`, however,  this can be overridden by changing `include_defaults` to `true`.

