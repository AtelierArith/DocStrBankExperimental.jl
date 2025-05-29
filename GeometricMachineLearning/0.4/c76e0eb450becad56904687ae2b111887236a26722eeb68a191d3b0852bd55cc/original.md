```
solve!(nn::NeuralNetwork{<:PSDArch}, input)
```

Solve the cotangent lift problem for an input.

[`PSDArch`](@ref) does not require neural network training since it is a strictly linear operation that can be solved with singular value decomposition (SVD).
