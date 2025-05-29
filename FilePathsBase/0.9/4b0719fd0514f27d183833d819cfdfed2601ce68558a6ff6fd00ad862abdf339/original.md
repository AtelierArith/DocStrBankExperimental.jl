```
cp(src::AbstractPath, dst::AbstractPath; force=false, follow_symlinks=false)
```

Copy the file or directory from `src` to `dst`. An existing `dst` will only be overwritten if `force=true`. If the path types support symlinks then `follow_symlinks=true` will copy the contents of the symlink to the destination.
