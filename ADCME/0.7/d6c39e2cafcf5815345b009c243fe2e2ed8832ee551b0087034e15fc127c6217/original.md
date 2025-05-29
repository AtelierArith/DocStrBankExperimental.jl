```
ae(x::Union{Array{Float64}, PyObject}, 
    output_dims::Array{Int64}, 
    θ::Union{Array{Array{Float64}}, Array{PyObject}};
    activation::Union{Function,String} = "tanh")
```

Alias: `fc`, `ae`

Constructs a neural network with given weights and biases `θ`

# Example

```julia
x = constant(rand(10,30))
θ = ae_init([30, 20, 20, 5])
y = ae(x, [20, 20, 5], θ) # 10×5
```
