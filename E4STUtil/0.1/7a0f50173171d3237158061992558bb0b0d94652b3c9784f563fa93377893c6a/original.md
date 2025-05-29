```
save_metadata(file::String, description::String) -> metadata
```

Saves metadata for `file` to `joinpath(dirname(file), "metadata.yml")`, making it if needed.
