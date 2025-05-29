```
generate_sources(model, cosmo, halo_pos_inp, halo_mass_inp; verbose=true)
```

Produce a source catalog from a model and halo catalog. This converts the halo arrays into the type specified by `model`.

# Arguments:

  * `model::AbstractCIBModel{T}`: source model parameters
  * `cosmo::Cosmology.FlatLCDM{T}`: background cosmology
  * `Healpix_res::Resolution`: Healpix map resolution
  * `halo_pos_inp::AbstractArray{TH,2}`: halo positions with dims (3, nhalos)
  * `halo_mass_inp::AbstractArray{TH,1}`: halo masses

# Keywords

  * `verbose::Bool=true`: print out progress details
