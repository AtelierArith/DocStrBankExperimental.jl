```
NetworkArg(
    model::BiophysicalModel
    protocol::Protocol
    params::Tuple{Vararg{String}}
    prior_range::Tuple{Vararg{Tuple{Float64,Float64}}} # range for priors 
    prior_dist::Tuple{Vararg{<:Any}}
    paralinks::Tuple{Vararg{Pair{String,<:String}}} = ()
    noise_type::String = "Gaussian" # "Rician"    
    sigma_range::Tuple{Float64, Float64}
    sigma_dist::Distribution
    nsamples::Int64
    nin::Int64
    nout::Int64
    hidden_layers::Tuple{Vararg{Int64}}
    dropoutp::Union{<:AbstractFloat, Tuple{Vararg{<:AbstractFloat}}}
    actf::Function
)
```

Return a `NetworkArg` object with necessary parameters to construct a neural network model  and generate training samples for specifc biophysical model. A test network architecture and training samples can be automaticlly determined from the modelling task by using function

```
NetworkArg(model, protocol, params, prior_range, prior_dist, paralinks, noisetype, sigma_range, sigma_dist)
```
