```
train!(loss, Duplicated(model), data, opt_state)
```

This method uses Enzyme.jl instead of Zygote.jl to compute the gradients, but is otherwise the same as `train!(loss, model, data, opt_state)`.

Only available when Enzyme is loaded.

!!! compat "New"
    This method was added in Flux 0.13.9.

