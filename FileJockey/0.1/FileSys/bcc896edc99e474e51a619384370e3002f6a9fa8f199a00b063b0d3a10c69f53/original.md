```
getfiles(X)
```

Filters only file-like entries (regular files or symlink-to-files); then follows all symlinks. Results are `FileEntry`s only.

Shortcut for `X |> filter(isfile) |> map(follow)` (with `import CommandLiner.Iter.Hack: filter, map` for currying).
