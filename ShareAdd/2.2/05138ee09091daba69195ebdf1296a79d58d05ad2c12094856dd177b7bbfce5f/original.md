```
make_current_mnf(path_or_name) -> path
make_current_mnf(; current::Bool) -> path
make_current_mnf(env::EnvInfo) -> path
```

Creates a [versioned manifest](https://pkgdocs.julialang.org/v1/toml-files/#Different-Manifests-for-Different-Julia-versions)

If called `make_current_mnf(; current=true)`, the current environment will be processed by this function. 

`path_or_name` can name of a shared environment starting with `@`, or a path to any environment.

  * If currently executed Julia version doesn't support version-specific manifests, do nothing.
  * Else, if a versioned manifest for current Julia already exists, do nothing.
  * Else, if the environment is the main shared env for the current Julia version (e.g. "@v1.11" for Julia v1.11), do nothing.
  * Else, is a (versioned) manifest for an older Julia exists in the given directory, copy it to a file named according to the current Julia version, e.g. `Manifest-v1.11.toml`.
  * Else, create empty one.

Returns path to the created or existing manifest.

This function is public, not exported.
