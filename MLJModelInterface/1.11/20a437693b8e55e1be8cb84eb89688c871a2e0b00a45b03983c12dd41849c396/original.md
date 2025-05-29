```
MLJModelInterface.reformat(model, args...) -> data
```

Models optionally overload `reformat` to define transformations of user-supplied data into some model-specific representation (e.g., from a table to a matrix). When implemented, the MLJ user can avoid repeating such transformations unnecessarily, and can additionally make use of more efficient row subsampling, which is then based on the model-specific representation of data, rather than the user-representation. When `reformat` is overloaded, `selectrows(::Model, ...)` must be as well (see [`selectrows`](@ref)). Furthermore, the model `fit` method(s), and operations, such as `predict` and `transform`, must be refactored to act on the model-specific representations of the data.

To implement the `reformat` data front-end for a model, refer to "Implementing a data front-end" in the [MLJ manual](https://juliaai.github.io/MLJ.jl/dev/adding_models_for_general_use/).
