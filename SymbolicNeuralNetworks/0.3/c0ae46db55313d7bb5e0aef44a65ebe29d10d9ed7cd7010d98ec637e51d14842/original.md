```
SymbolicPullback <: AbstractPullback
```

`SymbolicPullback` computes the *symbolic pullback* of a loss function.

# Examples

```jldoctest
using SymbolicNeuralNetworks
using AbstractNeuralNetworks
using AbstractNeuralNetworks: params
import Random
Random.seed!(123)

c = Chain(Dense(2, 1, tanh))
nn = NeuralNetwork(c)
snn = SymbolicNeuralNetwork(nn)
loss = FeedForwardLoss()
pb = SymbolicPullback(snn, loss)
ps = params(nn)
typeof(pb(ps, nn.model, (rand(2), rand(1)))[2](1))

# output

@NamedTuple{L1::@NamedTuple{W::Matrix{Float64}, b::Vector{Float64}}}
```

# Implementation

An instance of `SymbolicPullback` stores

  * `loss`: an instance of a `NetworkLoss`,
  * `fun`: a function that is used to compute the pullback.

If we call the functor of an instance of `SymbolicPullback` on `model`, `ps` and `input` it returns:

```julia
_pullback.loss(model, ps, input...), _pullback.fun(input..., ps)
```

where the second output argument is again a function.

# Extended help

We note the following seeming peculiarity:

```jldoctest
using SymbolicNeuralNetworks
using AbstractNeuralNetworks: Chain, Dense, NeuralNetwork, FeedForwardLoss, params
using Symbolics
import Random
Random.seed!(123)

c = Chain(Dense(2, 1, tanh))
nn = NeuralNetwork(c)
snn = SymbolicNeuralNetwork(nn)
loss = FeedForwardLoss()
pb = SymbolicPullback(snn, loss)
input_output = (rand(2), rand(1))
loss_and_pullback = pb(params(nn), nn.model, input_output)
# note that we apply the second argument to another input `1`
pb_values = loss_and_pullback[2](1)

@variables soutput[1:SymbolicNeuralNetworks.output_dimension(nn.model)]
symbolic_pullbacks = SymbolicNeuralNetworks.symbolic_pullback(loss(nn.model, params(snn), snn.input, soutput), snn)
pb_values2 = build_nn_function(symbolic_pullbacks, params(snn), snn.input, soutput)(input_output[1], input_output[2], params(nn))

pb_values == (pb_values2 |> SymbolicNeuralNetworks._get_contents |> SymbolicNeuralNetworks._get_params)

# output

true
```

See the docstrings for [`symbolic_pullback`](@ref), [`build_nn_function`](@ref), [`_get_params`](@ref) and [`_get_contents`](@ref) for more info on the functions that we used here. The noteworthy thing in the expression above is that the functor of `SymbolicPullback` returns two objects: the first one is the loss value evaluated for the relevant parameters and inputs. The second one is a function that takes again an input argument and then finally returns the partial derivatives. But why do we need this extra step with another function?

!!! info "Reverse Accumulation"
    In machine learning we typically do [reverse accumulation](https://en.wikipedia.org/wiki/Automatic_differentiation#Forward_and_reverse_accumulation) to perform automatic differentiation (AD). Assuming we are given a function that is the composition of simpler functions $f = f_1\circ{}f_2\circ\cdots\circ{}f_n:\mathbb{R}^n\to\mathbb{R}^m$ *reverse differentiation* starts with *output sensitivities* and then successively feeds them through $f_n$, $f_{n-1}$ etc. So it does:

    $$
    (\nabla_xf)^T = (\nabla_{x}f_1)^T(\nabla_{f_1(x)}f_2)^T\cdots(\nabla_{f_{n-1}(\cdots{}x)}f_n)^T(do),
    $$

    where $do\in\mathbb{R}^m$ are the *output sensitivities* and the jacobians are stepwise multiplied from the left. So we propagate from the output stepwise back to the input. If we have $m=1$, i.e. if the output is one-dimensional, then the *output sensitivities* may simply be taken to be $do = 1$.


So in theory we could leave out this extra step: returning an object (that is stored in `pb.fun`) can be seen as unnecessary as we could simply store the equivalent of `pb.fun(1.)` in an instance of `SymbolicPullback`. It is however customary for a pullback to return a callable function (that depends on the *output sensitivities*), which is why we also choose to do this here, even if the *output sensitivities* are a scalar quantity.
