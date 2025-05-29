```
new_pkg(pkg, description, tags)
```

Create a new entry for a package on `TLDR.data` adding it in the correct order.

Some rules:

  * All entries should be strings, except for `tags` which is an array of strings.
  * `pkg` should be the case sensitive package name (no .jl), e.g. "TLDR".
  * `tags` shouldn't be empty.
