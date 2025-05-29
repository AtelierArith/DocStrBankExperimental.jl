```
create_my_artifact(f::Function)
```

Create artifact by calling `f(working_dir)`. `f` is the function that create/put/download file(s) into  the `working_dir`. `f` should either return the path to the file/directory or return `nothing`. If `f`  return `nothing`, then everything in `working_dir` would be cached. If `f` return a path, that path  must be inside `working_dir`.
