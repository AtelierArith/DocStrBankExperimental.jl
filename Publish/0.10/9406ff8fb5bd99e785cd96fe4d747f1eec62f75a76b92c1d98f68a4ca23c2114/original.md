```
deploy(
    source, [dir="."], [targets...=html];
    versioned=true,
    named=false,
    force=false,
    label=nothing,
)
```

Build the `source` using the given `targets` list in the `dir` directory. `source` can be either a `Module` or a `String` representing a `Project.toml` path.

Keyword arguments can be used to control resulting directory structure.

{#keywords}

  * `versioned` and `named`.

    These keywords will place the built files in either a versioned subdirectory, or a named subdirectory of `dir`, or both (with name superceding version).

    The values for `name` and `version` are taken from those provided in the project's `Project.toml` file. If these values are not specified then the "deployment" will fail.
  * `force` will remove the calculated build path prior to building if it already exists.
  * `label` specifies a temporal folder name to copy the finished build to. This can be used to build a "tracking" version of documentation such as a "dev" or "stable" that changes over time while still retaining the exact versioned builds.

## Examples

In the following examples our project will be the `Publish` package. This can be switched out for any other project source, such as a Julia package or a simple `Project.toml` file.

```julia
deploy(Publish, "build")
```

writes the output to the `"build"` subdirectory of the current directory. There will be a `build/<version>` folder containing HTML content.

```julia
deploy(Publish, "build", pdf)
```

does the same as above, but build the [`pdf`](#) output instead.

```julia
deploy(Publish, "all-docs", pdf, html)
```

or build everything at once.

The keyword arguments control other aspects of the build, as shown [above](#keywords). For example,

```julia
deploy(Publish, "ecosystem"; named=true)
```

would build `Publish` documentation to an `ecosystem/Publish/<version>` subdirectory.
