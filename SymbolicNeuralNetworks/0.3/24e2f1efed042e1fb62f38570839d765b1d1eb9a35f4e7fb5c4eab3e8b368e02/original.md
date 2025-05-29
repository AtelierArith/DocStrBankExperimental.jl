```
build_nn_function(eqs, nn, soutput)
```

Build an executable function that can also depend on an output. The resulting `built_function` is then called with:

```julia
built_function(input, output, ps)
```

Also compare this to [`build_nn_function(::EqT, ::AbstractSymbolicNeuralNetwork)`](@ref).

# Extended Help

See the *extended help section* of [`build_nn_function(::EqT, ::AbstractSymbolicNeuralNetwork)`](@ref).
