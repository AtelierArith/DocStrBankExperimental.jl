```
kick_start_compat(
    code_dir::String,
    julia_version = "1.5.4";
    exact_versions = false
)
```

Given a directory containing both a Project.toml and Manifest.toml, print a string of a suggested compat entry for all Project.toml dependencies. Set `exact_versions = true` for the printed compat entries to exactly match the manifest file.
