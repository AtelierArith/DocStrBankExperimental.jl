```
Marginal(data, is_clamped, is_initial, addons)
```

An implementation of a marginal in variational message passing framework.

# Arguments

  * `data::D`: marginal always holds some data object associated with it, which is usually a probability distribution
  * `is_clamped::Bool`, specifies if this marginal was the result of constant computations (e.g. clamped constants)
  * `is_initial::Bool`, specifies if this marginal was used for initialization
  * `addons::A`, specifies the addons of the marginal, which may carry extra bits of information, e.g. debug information, memory, etc.

# Example

```jldoctest
julia> distribution = Gamma(10.0, 2.0)
Distributions.Gamma{Float64}(α=10.0, θ=2.0)

julia> message = Marginal(distribution, false, true, nothing)
Marginal(Distributions.Gamma{Float64}(α=10.0, θ=2.0))

julia> mean(message) 
20.0

julia> getdata(message)
Distributions.Gamma{Float64}(α=10.0, θ=2.0)

julia> is_clamped(message)
false

julia> is_initial(message)
true
```
