```
ImplicitDistribution(sample_function, args...)
```

Define a distribution that can only be sampled from using `rand`, but has no explicit `pdf`.

Each time `rand(rng, d::ImplicitDistribution)` is called,

```julia
sample_function(args..., rng)
```

will be called to generate a new sample.

`ImplicitDistribution` is designed to be used with anonymous functions or the `do` syntax as follows:

# Examples

```julia
ImplicitDistribution(rng->rand(rng)^2)
```

```julia
struct MyMDP <: MDP{Float64, Int} end

function POMDPs.transition(m::MyMDP, s, a)
    ImplicitDistribution(s, a) do s, a, rng
        return s + a + 0.001*randn(rng)
    end
end

td = transition(MyMDP(), 1.0, 1)
rand(td) # will return a number near 2
```
