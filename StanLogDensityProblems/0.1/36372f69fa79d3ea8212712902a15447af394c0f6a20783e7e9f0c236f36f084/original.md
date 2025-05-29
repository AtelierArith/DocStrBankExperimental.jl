```
StanProblem(lib::String[, data::String[ seed::Int]]; nan_on_error::Bool=false, kwargs...)
```

Construct a [`BridgeStan.StanModel`](@extref) and wrap it as a `StanProblem`.

`lib` is a path either to a compiled Stan model or to a `.stan` file. For details on the arguments, see the docstring for [`BridgeStan.StanModel`](@extref).

!!! note
    By default, Stan does not compile the model with multithreading support. If this is needed, pass `make_args=["STAN_THREADS=true"]` to `kwargs`.

