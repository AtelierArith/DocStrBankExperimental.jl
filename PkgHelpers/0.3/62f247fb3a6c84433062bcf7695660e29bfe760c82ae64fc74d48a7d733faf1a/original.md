```
freeze(pkg; julia=juliaversion(), relaxed = false, copy_manifest=false)
```

Freezes the current package versions by adding them to the Project.toml file.

# Arguments

  * pkg:           the module Pkg
  * julia:         version string for Julia compatibility, e.g. "1" or "~1.8, ~1.9, ~1.10"
  * relaxed:       if set to `true`, the minor version number is omitted from the generated                  compat entries. This means, non-breaking minor updates are allowed.
  * copy_manifest: if `true`, create a copy of the current `Manifest.toml` file using                a naming scheme like "Manifest.toml-1.10-windows"
  * keep:          if `true` (deftault) any existing compat entries are kept as is (maybe reordered)

For strict compatibility only add the Julia versions you tested your project with.

# Examples

```julia-repl
using Pkg, PkgHelpers
freeze(Pkg, copy_manifest=true)
freeze(Pkg; julia="~1.9, ~1.10", copy_manifest=true)
```
