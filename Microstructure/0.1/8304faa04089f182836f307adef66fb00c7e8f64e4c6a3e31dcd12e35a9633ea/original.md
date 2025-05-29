This method runs multi-threads MCMC estimation on dMRI data using a specified biophysical model, calls the voxel threading  method and save estimated parameters as nifti files. `savedir` includes both output path and file name prefix. Two-stage MCMC sampling methods are run if provided sampler is a Tuple of two samplers, where it will sample all the unknown parameters  using the first sampler then sample target tissue parameters in the second sampler while fixing the rest parameters to posterior means in the first MCMC.  

```
threading(
    model_start::BiophysicalModel,
    sampler::Union{Sampler,Tuple{Sampler,Sampler}},
    dmri::MRI,
    mask::MRI,
    protocol::Protocol,
    noise_model::Noisemodel,
    savedir::String,
)
```

Methods that return mean and standard deviation of estimations from measurements array of size [Nmeas, Nvoxels] using single-stage or two-stage MCMC.

```
threading(
    model_start::BiophysicalModel,
    sampler::Sampler,
    measurements::Array{Float64,2},
    protocol::Protocol,
    noise_model::Noisemodel,
)


threading(
    model_start::BiophysicalModel,
    sampler::Tuple{Sampler,Sampler},
    measurements::Array{Float64,2},
    protocol::Protocol,
    noise_model::Noisemodel,
)
```
