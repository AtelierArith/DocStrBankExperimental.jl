```
@neuralflux(eq::Expr)
```

Create a `NeuralFlux` using the syntax: `output ~ chain(inputs)`, where:

  * `output` is the output variable or a vector of output variables
  * `~` is the separator
  * `chain` is a Lux neural network chain
  * `inputs` is a vector of input variables

# Examples

```julia
@variables x, y, z
chain = Chain(Dense(2 => 10, relu), Dense(10 => 1), name=:my_net)

# Create a neural flux with a single output
flux1 = @neuralflux z ~ chain([x, y])

# Create a neural flux with multiple outputs
chain2 = Chain(Dense(2 => 16, relu), Dense(16 => 2), name=:multi_net)
flux2 = @neuralflux [z₁, z₂] ~ chain2([x, y])
```
