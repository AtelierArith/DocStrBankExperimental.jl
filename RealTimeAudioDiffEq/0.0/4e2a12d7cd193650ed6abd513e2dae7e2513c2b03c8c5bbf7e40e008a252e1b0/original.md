```
DESource(f, u0::Vector{Float64}, p::Vector{Float64};
	alg = Tsit5(), channel_map::Vector{Int} = [1, 1])::DESource
```

Create a DESource from an ODEFunction.

# Arguments

  * `f::ODEFunction`: the ODE function. Should be of the form `f(du, u, p, t)` (In-place).
  * `u0`: the array of initial values.
  * `p`: the array of parameters.

# Keyword Arguments

  * `alg::DEAlgorithm = Tsit5()`: the algorithm which will be passed to the solver.
  * `channel_map::Vector{Int} = [1, 1]`: the channel map indicates how system's variables should be mapped to output channels in the audio device. The position in the array represents the channel number and the value, the variable.
