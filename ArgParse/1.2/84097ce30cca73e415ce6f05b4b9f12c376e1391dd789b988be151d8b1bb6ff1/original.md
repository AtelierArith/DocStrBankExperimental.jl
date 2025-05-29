```
@project_version
@project_version(filename::String...)
```

Reads the version from the Project.toml file at the given filename, at compile time. If no filename is given, defaults to `Base.current_project()`. If multiple strings are given, they will be joined with `joinpath`. Intended for use with the [`ArgParseSettings`](@ref) constructor, to keep the settings version in sync with the project version.

## Example

```julia
ArgParseSettings(add_version = true, version = @project_version)
```
