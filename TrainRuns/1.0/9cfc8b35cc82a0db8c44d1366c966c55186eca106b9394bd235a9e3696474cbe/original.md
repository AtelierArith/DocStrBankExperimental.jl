```
trainrun(train::Train, path::Path, settings::Settings)
```

Calculate the running time of a `train` on a `path`. The `settings` provides the choice of models for the calculation. `settings` can be omitted. If so, a default is used. The running time will be return in seconds.

# Examples

```julia-repl
julia> trainrun(train, path)[end,:t]
xxx.xx # in seconds
```
