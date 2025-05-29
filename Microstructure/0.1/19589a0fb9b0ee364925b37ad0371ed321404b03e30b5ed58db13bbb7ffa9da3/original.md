```
pre_allocate(
    model::BiophysicalModel, sampler::Sampler, datasize::Tuple{Int64,Int64}
)

pre_allocate(
    model::BiophysicalModel, sampler::Tuple{Sampler,Sampler}, datasize::Tuple{Int64,Int64}
)
```

Allocating spaces for caching computing results based on `model`, `sampler` and `datasize`. `datasize` is the size of data (Nmeas, Nvoxels) 
