```
compute(args...; ctx=default_scheduler(), kwargs...) -> Any
```

Compute the value of a lazy tensor. The result is the argument itself, or a tuple of arguments if multiple arguments are passed. Some keyword arguments can be passed to control the execution of the program:     - `verbose=false`: Print the generated code before execution     - `tag=:global`: A tag to distinguish between different classes of inputs for the same program.
