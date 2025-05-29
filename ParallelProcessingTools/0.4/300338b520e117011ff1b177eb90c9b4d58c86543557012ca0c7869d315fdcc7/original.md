```
CreateOrIgnore() isa WriteMode
```

Indicates that new files should be created, and that nothing should be done if if the files already exist.

Causes an error to be thrown if only some of the files exist, to indicate an inconsistent state.

`CreateOrIgnore()` is the recommended default when creating files in a parallel computing context, especially if failure or timeouts might result in re-tries. This way, if multiple workers try to create the same file(s), only one file or consistent set of files will be created under the target filenames.

See [`WriteMode`](@ref) and [`write_files`](@ref).
