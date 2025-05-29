```
new_snippet(cmd, description, tags)
new_snippet(pkg, cmd, description, tags)
```

Create a new snippet entry on `TLDR.data` adding it in the correct order. If the snippet depends on a package to work, then `pkg` should be passed.

Some rules:

  * All entries should be strings, except for `tags` which is an array of strings.
  * `pkg` should be the case sensitive package name (no .jl), e.g. "TLDR".
  * `tags` shouldn't be empty.
