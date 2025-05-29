```
DirectorySource(path::String; target::String = basename(path), follow_symlinks=false)
```

Specify a local directory to mount from `path`.

The content of the directory will be mounted in `${WORKSPACE}/srcdir`, or in its subdirectory pointed to by the optional keyword `target`, if provided. Symbolic links are replaced by a copy of the target when `follow_symlinks` is `true`.
