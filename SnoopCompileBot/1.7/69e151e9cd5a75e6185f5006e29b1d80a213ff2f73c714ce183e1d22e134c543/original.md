Returns a package's path without loading the package in the main Julia process. May launch a separate Julia process to find the package.

# Examples

```julia
pathof_noload("MatLang")
```
