```
getroot(p::Path, root = p.path)
```

Return the path for a `Path` object `p`, as if it were located in folder `root`. If `p` corresponds to a folder, return `root`. If `p` corresponds to a file `filename`, return `joinpath(root, filename)`.

!!! warning
    The result of `getroot` is not necessarily an existing path. This function is mostly useful to get information about `p` (e.g., its extension) without interacting with the filesystem.

