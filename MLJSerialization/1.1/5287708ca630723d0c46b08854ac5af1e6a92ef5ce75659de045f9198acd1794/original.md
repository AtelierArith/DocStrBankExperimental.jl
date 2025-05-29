```
Save(filename="machine.jlso"; kwargs...)
```

An iteration control, as in, `Save("run3/machine.jlso", compression=:gzip)`. 

Save the current state of the machine being iterated to disk, using the provided `filename`, decorated with a number, as in "run3/machine_42.jlso". The specified `kwargs` are passed to the model-specific serializer (JLSO for most Julia models).

For more on what is meant by "the machine being iterated", see [`IteratedModel`](@ref).
