```
merge_toml_files(filepaths; override)
```

Parses and merges all of the given TOML filepaths and returns them as a Dict. This allows a toml_dict to be constructed from multiple TOML files. By default, non-unique TOML entries are not allowed, but this can be changed by setting `override = true`.
