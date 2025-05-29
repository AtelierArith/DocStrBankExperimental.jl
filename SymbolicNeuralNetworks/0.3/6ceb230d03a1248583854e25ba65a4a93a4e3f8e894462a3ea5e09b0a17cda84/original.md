```
build_nn_function(eq, nn)
```

Build an executable function based on a symbolic equation, a symbolic input array and a [`SymbolicNeuralNetwork`](@ref).

This function can be called with:

```julia
built_function(input, ps)
```

# Implementation

Internally this is calling [`_build_nn_function`](@ref) and then *parallelizing* the expression via the index `k`.

# Extended Help

The functions mentioned in the implementation section were adjusted ad-hoc to deal with problems that emerged on the fly.  Other problems may occur. In case you bump into one please [open an issue on github](https://github.com/JuliaGNI/SymbolicNeuralNetworks.jl/issues).
