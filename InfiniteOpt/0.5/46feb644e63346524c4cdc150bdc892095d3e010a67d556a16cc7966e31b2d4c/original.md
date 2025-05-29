```
JuMP.backend(model::InfiniteModel)
```

Extend `backend` to return the `MathOptInterface` backend associated with the  optimizer model. Note this will be empty if the optimizer model has not been  build yet.

**Example**

```julia-repl
julia> moi_model = backend(model);
```
