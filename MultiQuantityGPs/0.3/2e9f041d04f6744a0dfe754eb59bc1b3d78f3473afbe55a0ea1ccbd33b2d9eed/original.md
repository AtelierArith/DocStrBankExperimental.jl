```julia
MQGP(
    samples::AbstractArray{<:@NamedTuple{x::Tuple{Vector{Float64}, Int64}, y::Float64}};
    bounds,
    N,
    kernel,
    means_use,
    means_learn,
    noise_value,
    noise_learn,
    use_cond_pdf
) -> MultiQuantityGPs.MQGP{typeof(MultiQuantityGPs.Kernels.multiKernel)}

```

Creates and returns a MQGP with hyperparameters trained and conditioned on the samples given. Lower and upper bounds are used to initialize one of the hyperparameters.

A noise standard deviation can optionally be passed in either as a single scalar value for all samples or a vector of values, one for each sample.

# Examples

```julia
# create a MQGP
beliefModel = MQGP([prior_samples; samples]; bounds)
```
