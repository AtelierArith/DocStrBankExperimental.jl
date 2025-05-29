```
new_entry(pkg, kind, cmd, description, tags)
```

Create a new entry on `TLDR.data` adding it in the correct order. You probably want `new_pkg` or `new_snippet` instead.

Some rules:

  * All entries should be strings, except for `tags` which is an array of strings.
  * `pkg` should be the case sensitive package name (no .jl), e.g. "TLDR".
  * `kind` should be either `header` or `snippet`.
  * `tags` shouldn't be empty.
  * If `kind` is `header` then `cmd` should be "".
