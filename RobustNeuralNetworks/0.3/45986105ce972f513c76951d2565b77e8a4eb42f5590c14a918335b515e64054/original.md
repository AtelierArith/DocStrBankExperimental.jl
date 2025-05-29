```
SandwichFC((in, out), σ::F; <keyword arguments>) where F
```

Construct a non-expansive "sandwich layer" for a dense (fully-connected) LBDN.

A non-expensive layer is a layer with a Lipschitz bound of exactly 1. This layer is provided as a Lipschitz-bounded alternative to [`Flux.Dense`](https://fluxml.ai/Flux.jl/stable/models/layers/#Flux.Dense). Its interface and usage was intentionally designed to be very similar to make it easy to use for anyone familiar with Flux.

# Arguments

  * `(in, out)::Pair{<:Integer, <:Integer}`: Input and output sizes of the layer.
  * `σ::F=identity`: Activation function.

# Keyword arguments

  * `init::Function=Flux.glorot_normal`: Initialisation function for all weights and bias vectors.
  * `bias::Bool=true`: Include bias vector or not.
  * `output_layer::Bool=false`: Just the output layer of a dense LBDN or regular sandwich layer.
  * `T::DataType=Float32`: Data type for weight matrices and bias vectors.
  * `rng::AbstractRNG = Random.GLOBAL_RNG`: rng for model initialisation.

# Examples

We can build a dense LBDN directly using `SandwichFC` layers. The model structure is described in Equation 8 of [Wang & Manchester (2023)](https://proceedings.mlr.press/v202/wang23v.html).

```jldoctest
using Flux
using Random
using RobustNeuralNetworks

# Random seed for consistency
rng = Xoshiro(42)

# Model specification
nu = 1                  # Number of inputs
ny = 1                  # Number of outputs
nh = fill(16,2)         # 2 hidden layers, each with 16 neurons
γ = 5                   # Lipschitz bound of 5.0

# Set up dense LBDN model
model = Flux.Chain(
    (x) -> (√γ * x),
    SandwichFC(nu => nh[1], relu; T=Float64, rng),
    SandwichFC(nh[1] => nh[2], relu; T=Float64, rng),
    (x) -> (√γ * x),
    SandwichFC(nh[2] => ny; output_layer=true, T=Float64, rng),
)

# Evaluate on dummy inputs
u = 10*randn(rng, nu, 10)
y = model(u)

println(round.(y;digits=2))

# output

[4.13 4.37 3.22 8.38 4.15 3.71 0.7 2.04 1.78 2.64]
```

See also [`DenseLBDNParams`](@ref), [`DiffLBDN`](@ref).
