```
setup(dir)
```

Initialise a `Publish` project in the given directory `dir`, which is created if it does not already exist.

When `dir` has a Julia project structure with a `Project.toml` file then `Publish` is added to it's dependencies list, otherwise, if it is not a Julia package then a `Project.toml` file is created as well as a `README.md` file.

## Keywords

  * `pkg::Bool=true` can be set to `false` to disable all `Pkg` calls during use of `setup`.
