```
lower_bound(pkg; julia=nothing, relaxed = false, copy_manifest=false)
```

Adds the current package versions as lower bound to the compat section of the Project.toml file.

# Arguments

  * pkg:           the module Pkg
  * julia:         version string for Julia compatibility, e.g. "1" or "1.8"
  * relaxed:       if set to `true`, the minor version number is omitted                  from the generated compat entries.
  * copy_manifest: if `true`, create a copy of the current `Manifest.toml` file using                a naming scheme like "Manifest.toml-1.10-windows"
  * keep:          if `true` (deftault) any existing compat entries are kept as is (maybe reordered)

# Examples

```julia-repl
using Pkg
lower_bound(Pkg)
```
