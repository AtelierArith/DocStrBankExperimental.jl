```
unpackposterior(nsteps::Integer, chains::AbstractVector{<:Tuple{AbstractVector{<:Integer}, AbstractMatrix{<:Real}, AbstractMatrix{<:Real}, AbstractMatrix{<:Real}, AbstractMatrix{Bool}, AbstractMatrix{<:Real}}})
```

Calculate the unconditional posterior from the output of MCMCsampler. `chains` is the output of the sampler, `nsteps` is the number of MCMC samples. 
