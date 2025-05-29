```
DESource(f, g, u0::Vector{Float64}, p::Vector{Float64};
	alg = SOSRA(), channel_map::Vector{Int} = [1, 1])::DESource
```

Create a Stochastic DESource from a drift function and a noise function.
