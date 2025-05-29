```
@cm_component component_name(; props...) = "file_name.md"
```

Creates a new `@component` definition from a markdown file. The `CommonMark.jl` package is used to parsed and render the contents of the file hence that package must be installed as a dependency, since this features is provided via the package extension mechanism.

Just as with a regular `@component` you can provide `props` to a markdown component that will be used in any interpolated values (using the `CommonMark` `$` syntax for interpolation).

When `Revise.jl` is active and tracking the package which contains a `@cm_component` definition updates to the source markdown file are tracked and passed to `Revise` to perform code revision.
