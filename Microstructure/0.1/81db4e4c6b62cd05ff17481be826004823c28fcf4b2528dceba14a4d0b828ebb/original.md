```
generate_samples(
    model::BiophysicalModel,
    protocol::Protocol,
    params::Tuple{Vararg{String}},
    prior_range::Tuple{Vararg{Tuple{Float64,Float64}}}, 
    prior_dist::Tuple{Vararg{<:Any}},
    nsample::Int,
    paralinks::Union{Pair{String},Tuple{Vararg{Pair{String}}}},
    sigma_range::Tuple{Float64, Float64},
    sigma::Distribution,
    noise_type::String="Gaussian",
    rng_seed,
)
```

Generate and return training samples for a model using given priors of tissue parameters  and specified noise model (`"Gaussian"` or `"Rician"`) and noise level.
