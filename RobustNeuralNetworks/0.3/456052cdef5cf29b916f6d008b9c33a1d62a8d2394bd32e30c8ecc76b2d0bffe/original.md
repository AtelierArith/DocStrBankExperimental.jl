```
abstract type AbstractLBDN{T, L} end
```

Explicit parameterisation for Lipschitz-bounded deep networks.

```
(m::AbstractLBDN)(u::AbstractVecOrMat)
```

Call and `AbstractLBDN` model given inputs `u`.

If arguments are matrices, each column must be a vector of inputs (allows batch simulations).

# Examples

This example creates a dense [`LBDN`](@ref) using [`DenseLBDNParams`](@ref) and calls the model with some randomly generated inputs.

```jldoctest
using Random
using RobustNeuralNetworks

# Setup
rng = Xoshiro(42)
batches = 10
γ = 20.0

# Model with 4 inputs, 1 ouput, 4 hidden layers
nu, ny = 4, 1
nh = [5, 10, 5, 15]

lbdn_ps = DenseLBDNParams{Float64}(nu, nh, ny, γ; rng)
lbdn = LBDN(lbdn_ps)

# Evaluate model with a batch of random inputs
u = 10*randn(rng, nu, batches)
y = lbdn(u)

println(round.(y; digits=2))

# output

[-1.11 -1.01 -0.07 -2.25 -4.22 -1.76 -3.82 -1.13 -11.85 -3.01]
```
