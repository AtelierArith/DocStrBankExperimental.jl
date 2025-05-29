```
Save(filename="machine.jls")
```

An iteration control, as in, `Save("run3/machine.jls")`. 

Save the current state of the machine being iterated to disk, using the provided `filename`, decorated with a number, as in "run3/machine42.jls". The default behaviour uses the Serialization module but this can be changed by setting the `method=save_fn(::String, ::Any)` argument where `save_fn` is any serialization method. For more on what is meant by "the machine being iterated", see [`IteratedModel`](@ref).
