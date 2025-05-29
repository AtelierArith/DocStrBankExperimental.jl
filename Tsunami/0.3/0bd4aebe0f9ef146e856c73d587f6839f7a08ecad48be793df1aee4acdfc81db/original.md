```
on_before_update([callback,] model, trainer, out, grad)
```

Called before the call to `Optimisers.update!` that  applies the gradient `grad` to update the `model`'s parameters. `out` is the output of the last call to [`train_step`](@ref).
