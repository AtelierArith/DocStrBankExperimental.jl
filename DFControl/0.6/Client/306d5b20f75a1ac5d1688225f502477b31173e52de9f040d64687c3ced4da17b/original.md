```
load(server::Server, j::Job)
```

Tries to load the [`Job`](@ref) from `server` at directory `j.dir`. If no exact matching directory is found, a list of job directories that comprise `j.dir` will be returned.
