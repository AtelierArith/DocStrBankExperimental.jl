```
ae_num(output_dims::Array{Int64})
fc_num(output_dims::Array{Int64})
```

Estimates the number of weights and biases for the neural network. Note the first dimension should be the feature dimension (this is different from [`ae`](@ref) since in `ae` the feature dimension can be inferred), and the last dimension should be the output dimension. 

# Example

```julia
x = constant(rand(10,30))
θ = ae_init([30, 20, 20, 5])
@assert ae_num([30, 20, 20, 5])==length(θ)
y = ae(x, [20, 20, 5], θ)
```
