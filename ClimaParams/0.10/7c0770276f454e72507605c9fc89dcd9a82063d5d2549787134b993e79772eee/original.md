```
create_toml_dict(FT;
    override_file,
    default_file,
)
```

Creates a `ParamDict{FT}` struct, by reading and merging upto two TOML files or Julia Dicts with override information taking precedence over default information.
