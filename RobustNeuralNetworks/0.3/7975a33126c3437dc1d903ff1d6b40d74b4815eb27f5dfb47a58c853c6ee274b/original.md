```
abstract type AbstractREN end
```

Explicit parameterisation for recurrent equilibrium networks.

```
(m::AbstractREN)(xt::AbstractVecOrMat, ut::AbstractVecOrMat)
```

Call an  `AbstractREN` model given internal states `xt` and inputs `ut`. 

If arguments are matrices, each column must be a vector of states or inputs (allows batch simulations).

# Examples

This example creates a contracting [`REN`](@ref) using [`ContractingRENParams`](@ref) and calls the model with some randomly generated inputs. 

```jldoctest
using Random
using RobustNeuralNetworks

# Setup
rng = Xoshiro(42)
batches = 10
nu, nx, nv, ny = 4, 2, 20, 1

# Construct a REN
contracting_ren_ps = ContractingRENParams{Float64}(nu, nx, nv, ny; rng)
ren = REN(contracting_ren_ps)

# Some random inputs
x0 = init_states(ren, batches; rng)
u0 = randn(rng, ren.nu, batches)

# Evaluate the REN over one timestep
x1, y1 = ren(x0, u0)

println(round.(y1;digits=2))

# output

[-1.49 0.75 1.34 -0.23 -0.84 0.38 0.79 -0.1 0.72 0.54]
```

See also [`REN`](@ref), [`WrapREN`](@ref), and [`DiffREN`](@ref).
