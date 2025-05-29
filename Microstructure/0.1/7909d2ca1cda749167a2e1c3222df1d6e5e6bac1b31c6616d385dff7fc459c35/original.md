Method 1 generates pertubations within function, creates and returns a dict chain, and modify final model estimates in place. This method is useful in checking a few voxels, e.g. for quality of fitting, chain dignostics and optimizing sampler for models. 

```
mcmc!(
    estimates::BiophysicalModel,
    meas::Vector{Float64},
    protocol::Protocol,
    sampler::Sampler,
    noise::Noisemodel = Noisemodel(),
    rng::Int64 = 1
)
```

```julia-repl
julia> chain = mcmc!(estimates, measurements, protocol, sampler, noise_model, rng)
```

Method 2 takes `chain` and `pertubations` as input, mutating `chain` in place which can be used to calculate finial estimates and uncertainties.  This method is used for processing larger dataset, e.g. for whole-barin/slices.  This method is used together with multi-threads processing that pre-allocate spaces for caching chains, avoiding creating them for each voxel.  This method also reuses `pertubations` for faster computation speed; we usually use very large numbers of pertubations (e.g. ~10^4) to densely sample the proposal distributions. 

```
mcmc!(
    chain::Vector{Any},
    estimates::BiophysicalModel,
    meas::Vector{Float64},
    protocol::Protocol,
    sampler::Sampler,
    pertubations::Vector{Vector{Any}},
    noise::Noisemodel = Noisemodel()
)
```

```julia-repl
julia> mcmc!(chain, estimates, meas, protocol, sampler, pertubations, noise_model))
```

# References

For using MCMC in microsturcture imaging, here are some recommended references:

Behrens, T.E.J., Woolrich, M.W., Jenkinson, M., Johansen-Berg, H., Nunes, R.G., Clare, S., Matthews, P.M., Brady, J.M., Smith, S.M., 2003. Characterization and Propagation of Uncertainty in Diffusion-Weighted MR Imaging. Magn Reson Med 50, 1077–1088. https://doi.org/10.1002/MRM.10609

Alexander, D.C., 2008. A General Framework for Experiment Design in Diffusion MRI and Its Application in Measuring Direct Tissue-Microstructure Features. Magn Reson Med 60, 439–448. https://doi.org/10.1002/mrm.21646
