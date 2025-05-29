```
ae(x::Union{Array{Float64}, PyObject}, output_dims::Array{Int64}, θ::Union{Array{Float64}, PyObject};
activation::Union{Function,String, Nothing} = "tanh")
```

Alias: `fc`, `ae`

Creates a neural network with intermediate numbers of neurons `output_dims`. The weights are given by `θ`

# Example 1: Explicitly construct weights and biases

```julia
x = constant(rand(10,2))
n = ae_num([2,20,20,20,2])
θ = Variable(randn(n)*0.001)
y = ae(x, [20,20,20,2], θ)
```

# Example 2: Implicitly construct weights and biases

```julia
θ = ae_init([10,20,20,20,2]) 
x = constant(rand(10,10))
y = ae(x, [20,20,20,2], θ)
```

See also [`ae_num`](@ref), [`ae_init`](@ref).
