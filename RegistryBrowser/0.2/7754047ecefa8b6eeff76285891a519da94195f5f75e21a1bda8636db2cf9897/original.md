```
registrybrowser(packagepattern=""; registrypattern="")
```

Launch an interactive browser in the terminal, making it possible to look through all registries that are available to the Julia session and get information about all packages in these registries.

Calling this function with a `packagepattern` restricts the shown packages to packages whose names match `packagepattern`. Similarly, only registries whose names match `registrypattern` will be shown. `packagepattern` and `registrypattern` can be of either `AbstractString` or `Regex` type.
