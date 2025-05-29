```
canonicalize(path::AbstractPath) -> AbstractPath
```

Canonicalize a path by making it absolute, `.` or `..` segments and resolving any symlinks if applicable.

WARNING: Fallback behaviour ignores symlinks and should be extended for paths where symlinks are permitted (e.g., `SystemPath`s).
