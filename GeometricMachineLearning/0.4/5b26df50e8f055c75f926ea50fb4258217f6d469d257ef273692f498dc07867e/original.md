```
optimization_step!(o, λY, ps, dx)
```

Update the weights `ps` based on an [`Optimizer`](@ref), a `cache` and first-order derivatives `dx`.

`optimization_step!` is calling [`update!`](@ref) internally.  `update!` has to be implemented for every [`OptimizerMethod`](@ref).

# Arguments

All arguments into `optimization_step!` are mandatory:

1. `o::`[`Optimizer`](@ref),
2. `λY::NamedTuple`: this named tuple has the same keys as `ps`, but contains [`GlobalSection`](@ref)s,
3. `ps::NamedTuple`: the neural network parameters,
4. `dx::Union{NamedTuple, NeuralNetworkParameters}`: the gradients stores as a NamedTuple.

All the arguments are given as `NamedTuple`s  as the neural network weights are stores in that format.

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: params

l = StiefelLayer(3, 5)
ps = params(NeuralNetwork(Chain(l), Float32)).L1
cache = apply_toNT(MomentumCache, ps)
o = Optimizer(MomentumOptimizer(), cache, 0, geodesic)
λY = GlobalSection(ps)
dx = (weight = rand(Float32, 5, 3), )

# call the optimizer
optimization_step!(o, λY, ps, dx)

_test_nt(x) = typeof(x) <: NamedTuple

_test_nt(λY) & _test_nt(ps) & _test_nt(cache) & _test_nt(dx)

# output

true
```

# Extended help

The derivatives `dx` here are usually obtained via an AD routine by differentiating a loss function, i.e. `dx` is $\nabla_xL$.
