```
Message(data, is_clamped, is_initial, addons)
```

An implementation of a message in variational message passing framework.

# Arguments

  * `data::D`: message always holds some data object associated with it, which is usually a probability distribution, but can also be an arbitrary function
  * `is_clamped::Bool`, specifies if this message was the result of constant computations (e.g. clamped constants)
  * `is_initial::Bool`, specifies if this message was used for initialization
  * `addons::A`, specifies the addons of the message, which may carry extra bits of information, e.g. debug information, memory, etc.

# Example

```jldoctest
julia> distribution = Gamma(10.0, 2.0)
Distributions.Gamma{Float64}(α=10.0, θ=2.0)

julia> message = Message(distribution, false, true, nothing)
Message(Distributions.Gamma{Float64}(α=10.0, θ=2.0))

julia> mean(message) 
20.0

julia> getdata(message)
Distributions.Gamma{Float64}(α=10.0, θ=2.0)

julia> is_clamped(message)
false

julia> is_initial(message)
true

```
