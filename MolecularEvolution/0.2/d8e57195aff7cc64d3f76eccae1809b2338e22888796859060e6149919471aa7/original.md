```
metropolis_sample(
    initial_tree::FelNode,
    models::Vector{<:BranchModel},
    num_of_samples;
    bl_sampler::UnivariateSampler = BranchlengthSampler(Normal(0,2), Normal(-1,1))
    burn_in=1000, 
    sample_interval=10,
    collect_LLs = false,
    midpoint_rooting=false,
)
```

A convenience method. One step of the Metropolis algorithm is performed by calling [`nni_update!`](@ref) with `softmax_sampler` and [`branchlength_update!`](@ref) with `bl_sampler`.

# Additional Arguments

  * `bl_sampler`: Sampler used to drawn branchlengths from the posterior.
